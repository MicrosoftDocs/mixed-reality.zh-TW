---
title: Unity 的效能建議
description: 使用混合現實應用程式改善效能的 Unity 特有秘訣。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形，cpu，gpu，轉譯，垃圾收集，hololens
ms.openlocfilehash: 724ec24408e70360fda07c59a4ca2ffc30b49c1f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438125"
---
# <a name="performance-recommendations-for-unity"></a>Unity 的效能建議

本文是以[混合現實的效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重于 Unity 引擎環境的特定學習。

此外，我們也強烈建議開發人員審查[Unity 的建議環境設定一文](Recommended-settings-for-unity.md)。 本文包含一些內容，其中包含建立具效能的混合現實應用程式時的一些最重要場景設定。 其中一些建議的設定也會反白顯示在下方。

## <a name="how-to-profile-with-unity"></a>如何使用 Unity 進行分析

Unity 提供 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 內建功能，這是為您的特定應用程式收集寶貴效能見解的絕佳資源。 雖然可以在編輯器中執行分析工具，但這些計量並不代表真正的執行時間環境，因此應該謹慎使用這項結果。 建議您在裝置上執行時，從遠端分析應用程式，以取得最精確且可採取動作的深入解析。 此外，Unity 的[框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)也是一個非常強大且深入解析的工具，可供您使用。

Unity 提供的絕佳檔：
1) 如何[從遠端將 Unity profiler 連線至 UWP 應用程式](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何[使用 Unity Profiler 有效率地診斷效能問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 當 Unity Profiler 已連線，並在新增 GPU 分析工具之後（請參閱右上角的 [*新增 Profiler* ]），可以在分析工具中間分別看到 CPU & GPU 花費了多少時間。 這可讓開發人員在其應用程式為 CPU 或 GPU 界限時取得快速近似值。
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 效能建議

以下內容涵蓋更深入的效能實務，特別是針對 Unity & C#開發的目標。

#### <a name="cache-references"></a>快取參考

最佳做法是在初始化時快取所有相關元件和 Gameobject 的參考。 這是因為重複的函式呼叫（例如 *[GetComponent\<t > （））](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 相對於儲存指標的記憶體成本，會大幅提高成本。 這也適用于經常使用的[攝影機。](https://docs.unity3d.com/ScriptReference/Camera-main.html) *攝影機*實際上只會使用 *[FindGameObjectsWithTag （）](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，越低廉會在其中搜尋場景圖形中的攝影機物件是否有 *"MainCamera"* 標記。

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> 避免 GetComponent （字串） <br/>
> 使用 *[GetComponent （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 時，有少數不同的多載。 請務必一律使用型別式的實作為，而不是以字串為基礎的搜尋多載。 在場景中依字串搜尋會比依類型搜尋更為昂貴。 <br/>
> 充分元件 GetComponent （類型類型） <br/>
> 充分T GetComponent\<T > （） <br/>
> 形象元件 GetComponent （字串） > <br/>

#### <a name="avoid-expensive-operations"></a>避免耗費資源的作業

1) **避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    雖然 LINQ 可以非常簡潔且容易讀寫，但通常需要更多的計算，而且比手動撰寫演算法更多的記憶體配置。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **通用 Unity Api**

    某些 Unity Api 雖然很有用，但執行的成本可能很高。 其中大部分牽涉到搜尋整個場景圖形，以尋找一些相符的 Gameobject 清單。 這些作業通常可以藉由快取參考或針對有問題的 Gameobject 執行管理員元件來避免，以便在執行時間追蹤參考。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 應會以所有成本排除。 這些函數的順序可能會比直接函式呼叫的1000x 慢。

3) **注意裝箱**

    「[裝箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)」是C#語言和執行時間的核心概念。 這是將實數值型別變數（例如 char、int、bool 等）包裝成參考型別變數的程式。 當實值型別變數是「已裝箱」時，它會包裝在儲存在 managed 堆積上的 System.object 中。 因此，記憶體會被配置，而最終處置必須由垃圾收集行程處理。 這些配置和取消配置會產生效能成本，而且在許多情況下都不需要，也可以輕鬆地以較不昂貴的替代方案來取代。

    開發的其中一個最常見的裝箱形式是使用[可為 null 的實數值型別](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。 當作業嘗試取得值時，通常會想要能夠為函式中的實值型別傳回 null，特別是當作業失敗時。 這種方法的潛在問題是，配置現在會在堆積上進行，因此必須稍後再進行垃圾收集。

    **中的裝箱範例C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **透過可為 null 的實數值型別進行有問題之裝箱的範例**

    此程式碼示範一個可在 Unity 專案中建立的虛擬物件類別。 `TryGetSpeed()` 的呼叫將會導致堆積上的物件配置，而這將需要在稍後的時間點進行垃圾收集。 這個範例特別有問題，因為場景中可能有超過1000個以上的粒子，而每個都被要求其目前速度。 因此，1000個物件會被配置，因而解除配置每個畫面格，這會大幅降低效能。 重新撰寫函式以傳回負數值（例如-1）來表示失敗會避免這個問題，並將記憶體保留在堆疊上。

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>重複的程式碼路徑

任何重複的 Unity 回呼函數（亦即 Update），每秒執行的次數和/或框架應該非常小心地撰寫。 在此，任何耗費資源的作業都會對效能產生巨大且一致的影響。

1) **空白的回呼函數**

    雖然下列程式碼在您的應用程式中可能看似無害，特別是因為每個 Unity 腳本都會使用此程式碼區塊自動初始化，所以這些空白回呼實際上可能會變得非常昂貴。 Unity 會在非受控/managed 程式碼界限之間來回操作，在 UnityEngine 程式碼與您的應用程式程式碼之間。 即使沒有要執行的內容，透過此橋接器的內容切換也相當昂貴。 如果您的應用程式具有具有空白重複 Unity 回呼之元件的 100 Gameobject，這會變得特別有問題。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update （）是此效能問題最常見的表現，但其他重複的 Unity 回呼（例如下列情況）可能會同樣不好： FixedUpdate （）、LateUpdate （）、OnPostRender、OnPreRender （）、OnRenderImage （）等等。 

2) **針對每個框架執行一次的作業**

    下列 Unity Api 是許多全像攝影應用程式的常見作業。 雖然不一定能夠這麼做，但這些函式的結果通常會計算一次，並在整個應用程式中針對指定的框架重複使用結果。

    答）通常最好具有專用的單一類別或服務來處理場景中的注視 Raycast，然後在所有其他場景元件中重複使用此結果，而不是每個都有重複的 Raycast 作業。成分. 當然，有些應用程式可能需要從不同的來源或不同的[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)進行 raycasts。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b）藉由快取開始（）或喚醒（）中的[參考](#cache-references)，避免重複 Unity 回呼（例如 Update （））中的 GetComponent （）作業

        UnityEngine.Object.GetComponent()

    c）在初始化時將所有物件具現化，並在應用程式的整個執行時間使用[物件](#object-pooling)共用來回收並重複使用 gameobject 是很好的作法

        UnityEngine.Object.Instantiate()

3) **避免介面和虛擬結構**

    透過介面來叫用函式呼叫與直接物件或呼叫虛擬函式，通常比使用直接的結構或直接函式呼叫更耗費資源。 如果虛擬函式或介面不是必要的，則應該將它移除。 不過，這些方法的效能衝擊通常值得取捨，因為利用它們可簡化開發共同作業、程式碼可讀性和程式碼維護性。

    一般來說，建議您不要將欄位和函式標示為虛擬，除非有清楚的預期需要覆寫這個成員。 對於在每個畫面上多次呼叫的高頻率程式碼路徑，或甚至是每個畫面格（例如 `UpdateUI()` 方法），應該特別小心一次。

4) **避免以傳值方式傳遞結構**

    不同于類別，結構是實數值型別，而當直接傳遞至函式時，會將其內容複寫到新建立的實例。 此複本會增加 CPU 成本以及堆疊上的額外記憶體。 針對小型結構，效果通常非常小，因此可接受。 不過，對於重複叫用每個框架的函式，以及接受大型結構的函式，如果可能的話，請修改函式定義以傳址方式傳遞。 [在這裡深入瞭解](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>其他

1) **物理**

    答）一般而言，改善物理的最簡單方式是限制花費在物理上的時間量，或每秒的反覆運算次數。 當然，這會降低模擬準確度。 請參閱 Unity 中的[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)

    b） Unity 中的 colliders 類型具有廣為不同的效能特性。 下列順序列出從左至右到最低效能 colliders 的最高效能 colliders。 最重要的是避免網格 Colliders，這比基本 Colliders 高得多。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    如需詳細資訊，請參閱[Unity 物理最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)

2) **動態**

    停用閒置動畫，方法是停用 Animator 元件（停用遊戲物件不會有相同的效果）。 避免 animator 位於迴圈中的設計模式，將值設定為相同的內容。 這項技術會有相當大的負擔，對應用程式沒有任何影響。 [在這裡深入瞭解。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雜演算法**

    如果您的應用程式使用複雜的演算法，例如反向運動、路徑尋找等等，則尋找尋找較簡單的方法，或調整其效能的相關設定

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU 到 GPU 效能建議

一般來說，CPU 到 GPU 的效能會下降到提交給圖形配接器的**繪製呼叫**。 若要改善效能，必須將繪製呼叫視為策略性**的）減少**或**b）** ，以獲得最佳結果。 由於繪製呼叫本身會耗用大量資源，因此減少它們會降低所需的整體工作量。 此外，在繪製呼叫之間的狀態變更，在圖形驅動程式中需要昂貴的驗證和轉譯步驟，因此，重建應用程式的繪製呼叫來限制狀態變更（亦即 不同的材料等）可以提升效能。

Unity 有一篇很棒的文章，可讓您大致瞭解並探討其平臺的批次處理繪製呼叫。
- [Unity 繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>單一傳遞實例轉譯

Unity 中的單一傳遞實例轉譯可讓您將每個眼睛的繪製呼叫縮小至一個實例繪製呼叫。 由於兩個繪製呼叫之間的快取一致性，因此也會改善 GPU 上的效能。

若要在 Unity 專案中啟用這項功能
1)  開啟**播放 XR 設定**（移至 [**編輯**] > **專案設定** > **Player** > [ **XR 設定**]）
2) 從 [**身歷聲轉譯方法**] 下拉式功能表選取 [**單一傳遞實例**] （必須核取 [**虛擬實境支援**] 核取方塊）

如需此轉譯方法的詳細資訊，請參閱 Unity 中的下列文章。
- [如何使用 advanced 身歷聲轉譯將 AR 和 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單一階段實例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果開發人員已經有不為實例撰寫的現有自訂著色器，就會發生單一階段實例轉譯的一個常見問題。 啟用這項功能之後，開發人員可能會注意到有些 Gameobject 只會以一眼呈現。 這是因為相關聯的自訂著色器沒有適當的實例屬性。
>
> 如需解決此問題的方式，請參閱從 Unity 的[HoloLens 的單次傳遞身歷聲](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)轉譯

#### <a name="static-batching"></a>靜態批次處理

Unity 能夠批次處理許多靜態物件，以減少對 GPU 的繪製呼叫。 靜態批次處理適用于 Unity[中大部分的](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器物件**1）共用相同的**資料， **2）全部標示為*靜態*** （在 unity 中選取物件，然後按一下偵測器右上方的核取方塊）。 標記為*靜態*的 gameobject 無法在整個應用程式的執行時間移動。 因此，靜態批次處理可能很容易在 HoloLens 上運用，因為幾乎每個物件都必須放置、移動、調整等等。對於沉浸式耳機，靜態批次處理可以大幅減少繪製呼叫，因而改善效能。

如需詳細資訊，請參閱[Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的*靜態批次處理*。

#### <a name="dynamic-batching"></a>動態批次處理

由於將物件標示為靜態開發的*靜態*有問題，動態批次處理可能是補償這項缺少功能的絕佳工具。 當然，這也適用于沉浸式耳機。 Unity 中的動態批次處理可能會很困難，因為 Gameobject 必須**a）共用相同**的資料， **b）符合一長串的其他準則**。

如需完整清單，請閱讀在[Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)底下的*動態批次處理*。 最常見的情況是，Gameobject 因為相關聯的網格資料不能超過300的頂點而變成無效，而無法動態地進行批次處理。

#### <a name="other-techniques"></a>其他技術

只有在多個 Gameobject 可以共用相同的資料時，才會進行批次處理。 這通常會因為 Gameobject 的需求而遭到封鎖，其各自的材質具有獨特的材質。 通常會將材質結合成一個大材質，這是一種稱為[材質 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)的方法。

此外，通常最好是在可能和合理的情況下，將網格結合成一個 GameObject。 Unity 中的每個轉譯器都有相關聯的繪製呼叫，而不是在單一轉譯器下提交合併的網格。

>[!NOTE]
> 修改轉譯器的屬性。在執行時間時，會建立一份資料複本，因此可能會中斷批次處理。 使用轉譯器. sharedMaterial 來修改跨 Gameobject 的共用材質屬性。

## <a name="gpu-performance-recommendations"></a>GPU 效能建議

深入瞭解如何[優化 Unity 中的圖形呈現](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>優化深度緩衝區共用

通常建議您啟用 [**播放程式 XR 設定**] 底下的**深度緩衝區共用**，以優化[全息影像的穩定性](Hologram-stability.md)。 不過，使用此設定來啟用深度架構的延遲階段 reprojection 時，建議選取 [ **16 位深度格式**]，而不是 [ **24 位深度] 格式**。 16位深度緩衝區會大幅減少與深度緩衝區流量相關聯的頻寬（和電源）。 這在電源降低和效能改善方面都是一大優勢。 不過，有兩個可能的負面結果，其方式是使用*16 位深度格式*。

**Z-對抗**

較低的深度範圍精確度讓[z 對抗](https://en.wikipedia.org/wiki/Z-fighting)比24位更有可能發生在16位的情況下。 若要避免這些成品，請修改[Unity 攝影機](https://docs.unity3d.com/Manual/class-Camera.html)附近/遠的裁剪平面，以降低精確度。 對於 HoloLens 型應用程式，50m 的最大裁剪平面，而不是 Unity 預設1000m，通常可以排除任何 z 對抗。

**已停用樣板緩衝區**

當 Unity 建立[具有16位深度的呈現材質](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)時，並不會建立樣板緩衝區。 根據 Unity 檔選取24位深度格式時，將會建立24位的 z 緩衝區以及[8 位](https://docs.unity3d.com/Manual/SL-Stencil.html)的樣板緩衝區（如果32位適用于通常是 HoloLens 的案例）。

### <a name="avoid-full-screen-effects"></a>避免全螢幕效果

在全螢幕上操作的技術可能會相當耗費資源，因為其大小順序是每個框架的數百萬個作業。 因此，建議您避免[後續處理的效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)，例如消除鋸齒、bloom 等等。

### <a name="optimal-lighting-settings"></a>最佳光源設定

Unity 中的[即時全域照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供1-12 的視覺效果，但牽涉到相當昂貴的光源計算。 建議您透過**Window** ** > 轉譯** > **光源設定**，停用每個 Unity 場景檔案的即時全域照明，> 取消核取**即時全域照明**。

此外，建議您停用所有陰影轉換，因為這些也會在 Unity 場景上增加昂貴的 GPU 傳遞。 您可以針對每個光線停用陰影，但也可以透過品質設定來控制全面性地。

**編輯** > **專案設定**，然後選取 **品質** 類別 > 選取 UWP 平臺的 **低品質**。 您也可以只設定**shadows**屬性來**停用陰影**。

### <a name="reduce-poly-count"></a>減少 poly 計數

多邊形計數通常會縮減為
1) 從場景移除物件
2) 可減少指定網格多邊形數目的資產減去
3) 在您的應用程式中執行[層級的詳細資料（LOD）系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)，以相同幾何的較低多邊形版本呈現最遠的物件

### <a name="understanding-shaders-in-unity"></a>瞭解 Unity 中的著色器

比較效能中著色器的一個簡單近似值，就是識別每個在執行時間執行的平均作業數目。 這可以在 Unity 中輕鬆完成。

1) 選取您的著色器資產或選取材質，然後在 [偵測器] 視窗的右上角，選取齒輪圖示，然後按一下 [**選取著色器**]

    ![選取 Unity 中的著色器](images/Select-shader-unity.png)
2) 選取著色器資產後，按一下 [偵測器] 視窗底下的 [**編譯並顯示程式碼**] 按鈕

    ![在 Unity 中編譯著色器程式碼](images/compile-shader-code-unity.PNG)

3) 編譯之後，在結果中尋找 [統計資料] 區段，其中包含頂點和圖元著色器的不同作業數目（注意：圖元著色器通常也稱為片段著色器）

    ![Unity 標準著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>優化圖元著色器

使用上述方法查看已編譯的統計資料結果，[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會比端點[著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均執行更多作業。 片段著色器（也稱為圖元著色器）會針對螢幕輸出上的每個圖元執行，而頂點著色器只會針對繪製到螢幕的所有網格的每個頂點來執行。 

因此，由於所有光源計算，片段著色器通常會在較大的資料集上執行，因此不只會有比頂點著色器更多的指示。 例如，如果螢幕輸出是 2k by 2k 影像，則片段著色器可執行 2000 * 2000 = 4000000 次。 如果呈現兩眼，這個數位會加倍，因為有兩個畫面。 如果混合現實應用程式有多個階段、全螢幕後置處理效果，或將多個網格轉譯為相同的圖元，這個數位會大幅增加。 

因此，減少片段著色器中的作業數目，通常可以在端點著色器中提供比優化更佳的效能提升。

#### <a name="unity-standard-shader-alternatives"></a>Unity 標準著色器替代專案

您不需要使用以實體為基礎的轉譯（.PBR）或其他高品質的著色器，而是瞭解如何利用更高效能且更便宜的著色器。 [Mixed Reality 工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組提供已針對混合現實專案優化的[MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。

Unity 也提供 unlit、頂點亮、擴散和其他簡化的著色器選項，相較于 Unity 標準著色器，速度明顯更快。 如需詳細資訊，請參閱[內建著色器的使用方式和效能](https://docs.unity3d.com/Manual/shader-Performance.html)。

#### <a name="shader-preloading"></a>著色器預先載入

使用*著色器預先載入*和其他訣竅來優化[著色器載入時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。 特別是，著色器預先載入表示您不會因為執行時間著色器編譯而看到任何 hitches。

### <a name="limit-overdraw"></a>限制過度繪製

在 Unity 中，您可以切換**場景視圖**左上角的 [[**繪製模式] 功能表**](https://docs.unity3d.com/Manual/ViewModes.html)，然後選取 [**過度繪製**]，以顯示其場景的過度繪製。

一般來說，在將物件傳送至 GPU 之前，您可以先將它們先行剔除，藉以減輕過度繪製。 Unity 提供為其引擎執行[遮蔽剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的詳細資料。

## <a name="memory-recommendations"></a>記憶體建議

記憶體配置過多 & 解除配置作業可能會對您的全像攝影應用程式造成不良的影響，因而導致效能不一致、凍結的框架和其他有害行為。 在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。

#### <a name="garbage-collection"></a>垃圾收集

當 GC 啟動以分析不在執行期間的物件，而且需要釋放其記憶體以供重複使用時，全像攝影應用程式會將計算時間鬆散地處理到垃圾收集行程（GC）。 常數配置和取消配置通常需要垃圾收集行程執行得更頻繁，因此會影響效能和使用者體驗。

Unity 提供了絕佳的頁面，詳細說明垃圾收集行程的運作方式，以及在記憶體管理方面撰寫更有效率的程式碼的秘訣。
- [優化 Unity 遊戲中的垃圾收集](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

導致過多垃圾收集的其中一個最常見做法是不會快取 Unity 開發中元件和類別的參考。 任何參考都應該在開始（）或喚醒（）期間捕捉，然後在更新（）或 LateUpdate （）等功能中重複使用。

其他快速提示：
- 使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#類別，在執行時間以動態方式建立複雜字串
- 當不再需要 Log （）的呼叫時，請將其移除，因為它們仍然在應用程式的所有組建版本中執行
- 如果您的全像攝影應用程式通常需要大量的記憶體，請考慮在載入階段期間（例如，在呈現載入或轉換畫面時[ _**）呼叫 system.object**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)

#### <a name="object-pooling"></a>物件共用

物件共用是一種常用的技術，可降低連續配置 & 取消設定物件的成本。 這是藉由配置相同物件的大型集區，並重複使用此集區中的非作用中、可用的實例來完成，而不是在一段時間內不斷產生和終結物件。 物件集區非常適合在應用程式期間有變數存留期的重複使用元件。

- [Unity 中的物件共用教學課程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>啟動效能

您應該考慮使用較小的場景來啟動您的應用程式，然後使用 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 來載入場景的其餘部分。 這可讓您的應用程式盡可能快速地進入互動狀態。 請注意，當新場景啟動時可能會有大型的 CPU 尖峰，而且任何轉譯的內容可能會斷斷續續或有所不便。 解決這個情況的方法之一，就是在載入的場景上將 AsyncOperation allowSceneActivation 屬性設為 false，等待場景載入，將畫面清除為黑色，然後再設回 true 以完成場景啟用。

請記住，當啟動場景載入時，會向使用者顯示全像攝影啟動顯示畫面。

## <a name="see-also"></a>請參閱
- [優化 Unity 遊戲中的圖形轉譯](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [優化 Unity 遊戲中的垃圾收集](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [優化腳本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
