---
title: 了解效能 for Mixed Reality
description: 上的 Windows Mixed Reality 應用程式效能最佳化的進階主題和詳細資料
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: 混合實境、 混合的實境，虛擬實境、 VR、 MR、 效能、 最佳化、 CPU、 GPU 的 Windows
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596074"
---
# <a name="understanding-performance-for-mixed-reality"></a>混合實境的了解效能

這篇文章會介紹了合理化 Mixed Reality 應用程式效能的重要性。  如果不會執行您的應用程式，這是在最佳的畫面播放速率，就可以大幅降低使用者體驗。 全像投影會出現不穩定，因此前端追蹤環境的不正確導致體驗不佳的使用者。 事實上，效能必須視為 for Mixed Reality 開發與穩定、 週期工作的最後不使用的第一個類別功能。

供檢閱，如下所列每個目標平台的高效能的畫面播放速率值。

| 平台 | 目標畫面播放速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [電腦的 Windows Mixed Reality Ultra](immersive-headset-hardware-details.md) | 90 的 FPS |
| [混合實境電腦的 Windows](immersive-headset-hardware-details.md) | 60 FPS |

下列架構提供一般的外框的最佳作法，並了解內容，來達到目標畫面播放速率。 若要深入了解進一步詳細資料，請閱讀[Unity 文件的效能建議](performance-recommendations-for-unity.md)。 特別是，此相關的文章將討論如何測量您的 Unity Windows Mixed Reality 應用程式以及在 Unity 環境中採取以改善效能的步驟中的畫面播放速率。

## <a name="understanding-performance-bottlenecks"></a>了解效能瓶頸

如果您的應用程式有績效不佳的畫面播放速率，第一個步驟是分析，並了解您的應用程式的大量運算資源的位置。 有兩個主要的處理器負責轉譯場景的工作： 在 CPU 和 GPU。 這兩個元件的每個處理不同的作業與混合實境應用程式的階段。 有三個索引鍵的地方，可能會發生瓶頸。 

1. **應用程式執行緒-CPU** -此執行緒會負責您的應用程式邏輯。 這包括處理輸入、 動畫、 物理條件，以及其他應用程式的邏輯/狀態
2. **轉譯執行緒-CPU GPU** -這個執行緒負責提交您的繪製呼叫，以 GPU。 當您的應用程式想要轉譯的物件，例如 cube 或模型時，此執行緒就會傳送要求給 GPU，具有適用於轉譯的架構，以執行這些作業。
3. **GPU** - 
   此處理器通常會處理您的應用程式 （模型、 紋理等等） 的 3D 資料轉換為像素為單位，而且最後產生 2D 的映像，以提交至您的裝置 畫面的圖形管線。

![畫面格的存留期](images/lifetime-of-a-frame.png)

一般而言，HoloLens 的應用程式將會繫結的 GPU。 不過，這不會保留每個應用程式中，則為 true，因此建議使用的工具及技術下, 面以前往特定應用程式的地真。

## <a name="how-to-analyze-your-application"></a>如何分析您的應用程式

有許多工具可讓您身為開發人員若要了解您的混合實境應用程式的效能設定檔。 這些可讓您以這兩個您可在此有瓶頸，以及如何它們 manifesting 本身進行偵錯的目標。

這是常用且功能強大的工具，來取得深入分析您的應用程式資訊清單。
- [Intel 圖形效能分析器](https://software.intel.com/gpa)
- [Visual Studio 圖形偵錯工具](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何環境中的設定檔

沒有簡單的測試，來快速判斷 是否可能，繫結 GPU 或 CPU 繫結應用程式中。 如果您降低解析度轉譯目標輸出時，有較少的像素為單位來計算，因此，較少工作 GPU 必須執行才能呈現的影像。 檢視區縮放比例 （動態解析調整） 是呈現您的映像，以較小的做法呈現目標輸出裝置可以顯示。 裝置會增加取樣從一組較小的像素為單位來顯示最終的映像。

之後如果，請減少轉譯解析：
1) 應用程式畫面播放速率**增加**，您可能會**GPU 繫結**
1) 應用程式畫面播放速率**變**，您可能會**CPU 繫結**

>[!NOTE]
>Unity 讓您能夠輕鬆地修改您的應用程式，透過在執行階段的轉譯目標解析度*[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性。 在裝置上所呈現的最終映像有固定的解析度。 平台將範例建置在顯示器上呈現較高解析度影像輸出較低的解析度。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改善您的應用程式

### <a name="cpu-performance-recommendations"></a>CPU 效能建議

一般而言，在 CPU 上的混合的實境應用程式中的大部分工作牽涉到執行 「 模擬 」 的場景及處理大量的唯一應用程式邏輯。 因此，下列區域通常為目標進行最佳化。

- 動畫
- 簡化物理
- 記憶體配置
- 複雜的演算法 （也就是 反向運動、 路徑尋找）

### <a name="gpu-performance-recommendations"></a>GPU 效能建議

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解頻寬 vs 填滿率
轉譯 GPU 上的框架，應用程式時，通常是受限於記憶體頻寬或填滿率。

- **記憶體頻寬**是讀取的速率，並將寫入 GPU 可以從記憶體執行
    - 若要識別頻寬限制，減少紋理的品質，並檢查畫面播放速率獲得改善。
    - 在 Unity 中，做法是藉由變更**材質品質**中**編輯** > **專案設定** >   **[品質設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)**。
- **填滿率**指的是轉譯要在 gpu 每秒繪製的像素的輸送量。
    - 若要識別填滿速率限制，降低顯示器解析度，並檢查畫面播放速率獲得改善。 
    - 在 Unity 中，這可以透過*[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性

記憶體頻寬通常會涉及到最佳化
1) 減少紋理的解決方式
2) 使用較少的紋理 （亦即 法線反射，等等）

填滿率主要著重於降低作業需要計算最終呈現的像素數目。 這個範例通常分為減少
1) 要轉譯/處理序的物件數目
2) 每著色器的作業數目
3) 最終的結果 （幾何著色器後, 置處理效果等） 的 GPU 階段數目
4) 要呈現 （也就是像素數 顯示器解析度）

#### <a name="reduce-poly-count"></a>多邊計數減少
較高的多邊形計算中的 GPU 的更多作業的結果，並減少場景中的多邊形的數目會減少時間轉譯的幾何內。 還有其他因素也參與陰影的幾何，仍然十分耗費資源，但多邊形計數是基底的計量來判斷昂貴程度的場景會呈現。

#### <a name="limit-overdraw"></a>過度限制

最高過度繪製多個物件會轉譯，但因為它們由另一個、 一般接近 occluding 物件隱藏不輸出至畫面時，就會發生。 想像一下，看看的牆，有多個聊天室和其背後的幾何。 所有幾何的轉譯就會被處理，但不透明的牆，實際上需要轉譯為它 occludes 所有其他內容的檢視。 這會導致浪費資源的作業不需要目前的檢視。

#### <a name="shaders"></a>著色器

著色器是小型的程式在 GPU 上執行，並通常決定在轉譯的兩個重要步驟：
1) 應螢幕，以及它們的螢幕空間 （也就是中的位置上繪製哪些物件的頂點 端點著色器）
    - 頂點著色器通常針對每個 GameObject 執行每個頂點
2) 功能 （也就是這些像素的色彩 像素著色器）
    - 像素著色器會執行每個像素的裝置存在所呈現的材質

通常著色器所執行的許多轉換和光源計算。 雖然複雜光源模型、 陰影、 和其他作業可以產生絕佳的結果，它們也會隨附價格。 減少計算著色器的作業數目，可大幅減少每個畫面的 GPU 來完成所需的整體工作。

##### <a name="shader-coding-recommendations"></a>著色器程式碼的建議

- 使用雙線性篩選盡可能
- 重新排列為了同時執行 multiply 和新增使用瘋狂的內建函式的運算式
- 預先盡量在 CPU 上，並將資料傳遞為常數
- **偏好將作業從像素著色器移至頂點著色器**
    - 通常的頂點數目 << # 個像素為單位 （也就是 720p = = 921,600 像素為單位，1080p = = 2,073,600 像素為單位，依此類推)

#### <a name="remove-gpu-stages"></a>移除 GPU 階段
後置處理效果，可以是非常耗費資源，並通常禁止的應用程式的填滿率。 這也包括消除鋸齒的技術，例如 MSAA。 在 HoloLens，建議您使用完全避免這些技術。 此外，如果可能的話，應避免額外的著色器階段，例如幾何、 輪廓，以及計算著色器。

## <a name="memory-recommendations"></a>記憶體建議
過多的記憶體配置和解除配置作業可以有負面的影響，在您全像攝影版的應用程式，導致不一致的效能、 凍結的畫面格和其他有害的行為。 它是特別重要，因為記憶體管理由記憶體回收行程控制在 Unity 中開發時，了解記憶體考量。

#### <a name="object-pooling"></a>物件集區

物件共用便是常用的技巧來減少連續配置的成本和取消配置的物件。 這是所配置的相同物件的大型集區，並重複使用而不斷產生，並終結一段時間的物件不是此集區中的 非作用中、 可用的執行個體。 物件集區很適合重複使用變數的存留期期間應用程式的元件。

## <a name="see-also"></a>另請參閱
- [Unity 的效能建議](performance-recommendations-for-unity.md)
- [Unity 的建議的設定](recommended-settings-for-unity.md)
