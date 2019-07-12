---
title: Unity 的效能建議
description: 若要改善效能與混合的實境應用程式的 unity 特有秘訣。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形中，cpu、 gpu 轉譯，記憶體回收，hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843338"
---
# <a name="performance-recommendations-for-unity"></a>Unity 的效能建議

這篇文章是根據所述的討論[混合實境的效能建議](understanding-performance-for-mixed-reality.md)但著重於 Unity 引擎環境特有的做法。

它也是強烈建議開發人員檢閱[環境的建議設定是 Unity 文件](Recommended-settings-for-unity.md)。 這篇文章有內容，但是某些最重要的場景設定建置高效能 Mixed Reality 應用程式的相關事宜。 其中某些建議設定會反白顯示下面也。

## <a name="how-to-profile-with-unity"></a>如何使用 Unity 設定檔

Unity 提供 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 內建，也就是絕佳的資源來收集特定應用程式的重要效能深入解析。 雖然可以執行程式碼剖析工具編輯器內，這些度量不代表，則為 true 的執行階段環境，因此，從這個結果應小心。 建議從遠端設定檔應用程式時最精確且可付諸行動的深入解析的裝置上執行。 此外，Unity[框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)也是非常強大和深入解析 」 工具使用。

Unity 提供絕佳的文件：
1) 如何連接[UWP 應用程式的 Unity 分析工具從遠端](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何有效地[診斷效能問題與 Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 連線的 Unity Profiler 和加入 GPU 分析工具 (請參閱*新增 Profiler*在右上角)，可以看到多少時間花在 CPU 和 GPU 上分別中間程式碼剖析工具。 這可讓開發人員取得快速的近似值，它們的應用程式是否 CPU 或 GPU 繫結。
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 效能建議

以下內容涵蓋更多深入的效能做法，特別是針對 Unity （& s)C#開發。

#### <a name="cache-references"></a>快取的參考

它是最佳的作法，以在初始化的快取參考所有相關的元件和 Gameobject。 這是因為這類重複函式呼叫 *[GetComponent\<T > （)](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 成本遠相對於記憶體的指標儲存成本。 這也適用於以非常中，定期[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。 *Camera.main*實際上只會使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 低廉中搜尋您的場景圖形具有相機物件底下 *"MainCamera 」* 標記。

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
> Avoid GetComponent(string) <br/>
> 使用時 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* ，有少數幾個不同的多載。 請務必一律使用基礎的型別實作，而永遠不會以字串為基礎的搜尋多載。 根據在場景中的字串會大幅的成本高於搜尋型別。 <br/>
> （好）元件 GetComponent (類型 type) <br/>
> （好）T GetComponent\<T > （) <br/>
> （錯誤）元件 GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>避免耗費資源的作業

1) **請避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    雖然非常簡潔又方便讀取和寫入，可使用 LINQ，通常需要更多計算和特別更多的記憶體配置比手動寫出的演算法。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **常見的 Unity Api**

    特定的 Unity Api，雖然很實用，可以是執行代價很高。 其中大部分涉及搜尋整個場景圖形的一些符合 Gameobject 的清單。 這些作業通常可以避免快取的參考，或實作管理員元件的問題來追蹤在執行階段參考 Gameobject。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[Sendmessage （)](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 並 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 應該全力排除。 這些函式可以是大約 1000 x 低於直接函式呼叫。

3) **請注意 boxing**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是的核心概念C#語言和執行階段。 它會為參考型別變數包裝實值類型的變數，例如 char、 int、 bool 等程序。 當實值類型的變數為"boxed，時"會將它包裝在 System.Object 儲存在 managed 堆積上。 因此，配置的記憶體和最終處置時，才必須處理必要的記憶體回收行程。 這些配置和解除配置會產生效能成本和在許多情況下是不必要或可以輕鬆地取代成本較低的替代方案。

#### <a name="repeating-code-paths"></a>重複的程式碼路徑

任何重複的 Unity 回呼函數 （也就是 更新），每秒的次數執行及/或應該非常小心地寫入畫面格。 任何耗費資源的作業會對效能有很大且一致的影響。

1) **空白的回呼函式**

    下列程式碼看似無害將保留在您的應用程式，特別是因為每個 Unity 指令碼自動初始化此程式碼區塊時，雖然這些空白回呼可以實際成為非常耗費資源。 Unity 來回運作 UnityEngine 的程式碼和應用程式程式碼之間的 unmanaged/managed 程式碼界限。 切換此橋接器的內容就非常高昂，即使沒有任何項目執行。 這會成為您的應用程式是否有空白的重複 Unity 回呼的元件的 Gameobject 可擴充的特別有問題。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update （） 是此效能問題的最常見的現象，但其他重複的 Unity 回呼，如下所示可以同樣好到哪裡去如果不更差：FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **偏好執行一次作業每個畫面**

    下列的 Unity Api 是許多全像攝影版的應用程式的一般作業。 雖然不一定可行，這些函式的結果可以非常頻繁計算一次和結果重新利用指定的範圍內的應用程式。

    a） 通常最好有專用的單一類別或服務來處理您的視線 Raycast 場景，並接著在所有其他場景的元件，而不是由每個進行重複和基本上相同 Raycast 作業中重複使用此結果元件。 當然，有些應用程式可能需要來自不同的來源，或針對不同的 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b） 避免 GetComponent() 作業中重複的 Unity 回呼，例如 update （） 所[快取參考](#cache-references)start （） 或 Awake() 中

        UnityEngine.Object.GetComponent()

    c） 是很好的作法，所有物件，可能的話，請在初始設定和使用具現都化[物件集區](#object-pooling)回收，並重複使用整個應用程式的執行階段的 Gameobject

        UnityEngine.Object.Instantiate()

3) **避免介面和虛擬的建構**

    叫用函式呼叫，透過介面與直接物件或呼叫虛擬函式通常可以比使用直接建構或直接函式呼叫昂貴許多。 如果介面的虛擬函式是不必要的則應予以移除。 不過，效能的衝擊針對這些方法通常是值得取捨如果利用它們可簡化開發共同作業、 程式碼的可讀性及程式碼維護性。 

4) **值，以避免傳遞結構**

    不同於類別，結構是實值型別，並直接傳遞至函式，當其內容複製到新建立的執行個體。 此複本會將 CPU 成本以及其他在堆疊上的記憶體。 對於小型結構，結果會是通常很少，因此可接受。 不過，針對函式重複叫用每個畫面，以及採取大型結構的函式，如果可能的話修改以傳址方式傳遞的函式定義。 [進一步了解](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>其他

1) **物理**

    a） 一般，以改善物理的最簡單方式是時間的限制物理或每秒的次數所花費量。 當然，這會減少模擬精確度。 請參閱[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity 中

    在 Unity colliders b） 的類型有差異很大的效能特性。 下列順序列出從左到右以最少的高效能 colliders 大部分高效能 colliders。 它是最重要，以避免 Mesh Colliders 也就是比基本 colliders 更加昂貴。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    請參閱[Unity 物理最佳作法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)如需詳細資訊

2) **動畫**

    藉由停用動畫元件停用閒置的動畫 （停用遊戲物件將不會有相同的效果）。 請避免設計模式的動畫會位於迴圈，將值設定為相同的動作。 沒有針對此技術，不會影響應用程式使用大量的額外負荷。 [深入瞭解。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雜的演算法**

    如果您的應用程式使用反向運動、 路徑尋找等複雜的演算法，看起來以尋找更簡單的方法，或調整其效能的相關設定

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU-GPU 效能建議

一般而言，CPU-GPU 效能來到下移**繪製呼叫**送出至圖形卡。 若要改善效能，繪製呼叫必須是策略性**a） 減少**或**b） 重新編排**為獲得最佳結果。 由於繪製呼叫本身是需要大量資源，減少它們將會減少所需的整體工作。 此外，狀態 繪製呼叫之間的變更需要高成本的驗證和轉譯圖形驅動程式中的步驟，因此，重組您的應用程式繪製呼叫，以限制狀態變更 （亦即 不同的資料等），可以提升效能。

Unity 有一篇好文章，提供概觀，並探討其平台的繪製呼叫的批次。
- [Unity 繪製呼叫批次](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>單一行程的執行個體的轉譯

在 Unity 中的單一階段 Instanced 呈現可讓您降低下一個執行個體的繪製呼叫眼睛的繪製呼叫。 因為兩個繪製呼叫之間的快取一致性，另外還有一些效能改進，以及在 GPU 上。

若要啟用這項功能在您的 Unity 專案
1)  開啟**Player XR 設定**(前往**編輯** > **專案設定** > **Player**  > **XR 設定**)
2) 選取 **執行個體的單一傳遞**從**立體轉譯方法**下拉式選單 (**虛擬實境支援**必須選取核取方塊)

如需詳細資訊，此轉譯方法，從 Unity 閱讀下列文章。
- [如何使用進階的立體聲呈現的 AR 及 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單一行程的執行個體](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果開發人員已經不是針對撰寫的現有自訂著色器，就會發生一個常見的問題，使用單一傳遞執行個體轉譯執行個體。 之後啟用此功能，開發人員可能會注意到某些 Gameobject 唯一呈現，一眼中。 這是因為相關聯的自訂著色器沒有適當的屬性執行個體。
>
> 請參閱[單一傳遞是立體聲呈現 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)從 Unity 如何解決這個問題

#### <a name="static-batching"></a>靜態批次處理

Unity 是能夠減少 gpu 的繪製呼叫的許多靜態物件的批次。 靜態批次處理適用於大部分[轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)Unity 中的物件， **1） 共用相同的內容**並**2） 可以為所有標示*靜態*** (在 Unity 中選取物件，然後按一下右上角的核取方塊的 偵測器的權限)。 Gameobject 標示*靜態*無法移動整個應用程式的執行階段。 因此，靜態批次處理很難在何處放置時，移動、 縮放等幾乎每個物件的 HoloLens 上運用。沈浸式耳機，靜態批次處理可以大幅降低繪製呼叫並提升效能。

讀取*靜態批次處理*下方[繪製呼叫批次中 Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)如需詳細資訊。

#### <a name="dynamic-batching"></a>動態批次處理

因為它是將物件標示為有問題*靜態*HoloLens 開發動態批次處理可以是很棒的工具，可彌補這一點缺少功能。 當然，它是可以也是在沉浸式耳機也很有用。 在 Unity 中的動態批次處理很難透過啟用，因為必須 Gameobject **a） 共用相同的內容**並**b） 符合一長串的其他準則**。

讀取*動態批次處理*下方[繪製呼叫批次中 Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)的完整清單。 大多數情況下，Gameobject 變成無效，因為相關聯的網狀結構資料可能會不超過 300 個頂點動態批次處理。

#### <a name="other-techniques"></a>其他技術

批次只能執行多個 Gameobject 是否能夠共用相同的內容。 通常這將會封鎖 Gameobject 及其各自的資料有唯一的材質的需求。 通常會將紋理組合成一個大型的紋理，方法，也稱為[紋理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)。

此外，它通常最好是結合成一個 GameObject 網格，其中可能與合理。 在 Unity 中的每個轉譯器會將它與提交下一個轉譯器結合的網狀結構的繪製呼叫相關聯。 

>[!NOTE]
> 修改的屬性 Renderer.material 在執行階段會建立一份資料，並因此可能會中斷批次。 您可以使用 Renderer.sharedMaterial 共用的 material 屬性來修改整個 Gameobject。

## <a name="gpu-performance-recommendations"></a>GPU 效能建議

深入了解[最佳化 Unity 中的圖形轉譯](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 

### <a name="optimize-depth-buffer-sharing"></a>最佳化深度緩衝區共用

通常建議您啟用**深度緩衝區共用**下方**Player XR 設定**最佳化[全像穩定性](Hologram-stability.md)。 啟用時使用此設定，不過深度型晚期階段 reprojection，建議您選取**16 位元深度格式**而不是**24 位元深度格式**。 16 位元深度緩衝區將會大幅減少頻寬 （並因此 power） 與深度緩衝區流量相關聯。 這可以是一大電源大勝利，但僅適用於小型的深度範圍做為經驗[z 對抗](https://en.wikipedia.org/wiki/Z-fighting)更容易發生的 16 位元比 24 位元。 若要避免這些成品，修改的附近/遠裁剪平面[Unity 數位相機](https://docs.unity3d.com/Manual/class-Camera.html)負責的較低的有效位數。 HoloLens 為基礎的應用程式，而不使用 Unity 預設 1000 m 50m 遠裁剪平面通常可以排除任何 z 對抗。

### <a name="reduce-poly-count"></a>多邊計數減少

多邊形數目通常被減少
1) 移除場景中的物件
2) 可減少需要指定網格的多邊形的資產減去
3) 實作[層級的詳細資料 」 (LOD) 系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)到您的應用程式會呈現很遠的位置具有較低多邊形版本的相同 geometry 物件

### <a name="understanding-shaders-in-unity"></a>了解 Unity 中的著色器

簡單的概略比較效能的著色器是以識別每個作業的平均數目，在執行階段執行。 這都可以在 Unity 中輕鬆地完成。

1) 選取您的著色器資產或選取的資料，然後在右上角的 [偵測器] 視窗，選取齒輪圖示，然後 **"選取著色器 」**

    ![選取 在 Unity 中的 著色器](images/Select-shader-unity.png)
2) 與著色器資產選取的情況下，按一下 **「 編譯和顯示程式碼 」** 偵測器視窗底下的按鈕

    ![在 Unity 中的著色器程式碼編譯](images/compile-shader-code-unity.PNG)

3) 編譯之後，尋找在結果中的統計資料] 區段具有不同的作業，將 [頂點] 與 [像素著色器的數目 (注意： 像素著色器通常也稱為片段著色器)

    ![Unity 標準的著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>最佳化像素著色器

尋找已編譯的統計資料結果，使用上述方法[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會執行較多的作業，比[頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均。 片段著色器，也就是像素著色器，會執行每個輸出只執行每個頂點繪製到螢幕的所有網格的頂點著色器時在螢幕上的像素。 

因此，不只片段著色器沒有比 頂點著色器的詳細指示因為所有光源計算，片段著色器，幾乎一律會在較大的資料集上執行。 比方說，如果畫面輸出會是 2 個 k 映像的 2k，則片段著色器可以取得 2，000 * 2，000 = 4,000,000 執行一次時間。 如果呈現兩個的眼睛，這個數字會加倍，因為有兩個畫面。 如果混合的實境應用程式有多個傳遞、 全螢幕後置處理效果，或轉譯到相同的像素的多個節點網路，就會大幅增加這個數字。 

因此，減少片段著色器中的作業數目通常可更佳的效能提升於頂點著色器中的最佳化。

#### <a name="unity-standard-shader-alternatives"></a>Unity 標準的著色器的替代方案

而不是使用根據實際轉譯 (PBR) 或其他高品質的著色器，查看利用更好的效能和成本較低的著色器。 [混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供[MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)，已經過最佳化的混合的實境專案。

Unity 也提供光環、 頂點的光源、 擴散，並簡化著色器選項，速度明顯高於標準 Unity 著色器。 請參閱[使用量和效能的內建著色器](https://docs.unity3d.com/Manual/shader-Performance.html)如需詳細資訊。

#### <a name="shader-preloading"></a>預先載入的著色器

使用*著色器預先*和其他最佳化技巧[著色器載入時間](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。 特別的是，預先載入的著色器表示您不會看到任何 hitches 由於執行階段著色器編譯。

### <a name="limit-overdraw"></a>過度限制

在 Unity 中，一個可以顯示切換其場景，如過度[**繪製模式 功能表**](https://docs.unity3d.com/Manual/ViewModes.html)中的左上角**場景檢視**，然後選取**過度繪製**.

一般而言，過度繪製可減輕剔除事先，再傳送到 GPU 的物件。 Unity 提供詳細資料上實作[閉塞挑選](https://docs.unity3d.com/Manual/OcclusionCulling.html)其引擎。

## <a name="memory-recommendations"></a>記憶體建議

過多的記憶體配置和解除配置作業可以有負面的影響，在您全像攝影版的應用程式，導致不一致的效能、 凍結的畫面格和其他有害的行為。 它是特別重要，因為記憶體管理由記憶體回收行程控制在 Unity 中開發時，了解記憶體考量。

#### <a name="garbage-collection"></a>記憶體回收

分析執行期間不再是範圍內的物件，GC 會啟動，而且其記憶體需要釋出，因此它可以成為可供重複使用時，全像攝影版的應用程式將會遺失記憶體回收行程 (GC) 處理計算時間。 常數的配置和取消配置通常需要更頻繁地執行，因此影響效能和使用者體驗的記憶體回收行程。

Unity 提供一個絕佳的頁面，其中詳細說明記憶體回收行程的運作方式和撰寫更有效率的程式碼來管理記憶體的相關事宜的秘訣。
- [最佳化記憶體回收中的 Unity 遊戲](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

其中一個最常見的作法，會導致過多的記憶體回收不會快取元件和 Unity 開發中的類別的參考。 應該 start （） 或 Awake() 期間擷取和更新版本的函式，例如 update （） 或 LateUpdate() 中重複使用的任何參考。

其他的快速提示：
- 使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#以動態方式建立複雜的字串，在執行階段類別
- 移除對 Debug.Log() 不再需要仍在所有的組建版本的應用程式執行時呼叫
- 如果您全像攝影版的應用程式通常需要大量記憶體，請考慮呼叫[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)期間載入階段，例如呈現載入時或轉換畫面

#### <a name="object-pooling"></a>物件集區

物件共用便是常用的技巧來減少連續配置的成本和取消配置的物件。 這是所配置的相同物件的大型集區，並重複使用而不斷產生，並終結一段時間的物件不是此集區中的 非作用中、 可用的執行個體。 物件集區很適合重複使用變數的存留期期間應用程式的元件。

- [物件集區在 Unity 中的教學課程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>啟動效能

您應該考慮使用較小的場景，啟動您的應用程式，然後使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 載入場景的其餘部分。 這可讓您的應用程式，以前往 盡快互動狀態。 要注意，可能有大量的 CPU 使用量正在啟動新的場景時，與任何呈現的內容可能會斷斷續續或習以為常。 若要解決這個問題的一個方式是設為 false 的 AsyncOperation.allowSceneActivation 屬性上所載入的場景，等到場景方向，以載入，清除 為黑色，畫面，然後設為 true，以完成場景啟用回。

請記住，雖然在載入啟動場景全像攝影版的啟動顯示畫面將顯示給使用者。

## <a name="see-also"></a>另請參閱
- [最佳化 Unity 遊戲中的圖形轉譯](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [最佳化記憶體回收中的 Unity 遊戲](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理最佳作法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [最佳化指令碼 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
