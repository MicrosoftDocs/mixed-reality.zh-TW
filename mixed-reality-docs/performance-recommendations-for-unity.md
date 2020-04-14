---
title: 對 Unity 的效能建議
description: 使用混合實境應用程式改善效能的 Unity 特有秘訣。
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形, cpu, gpu, 轉譯, 記憶體回收行程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 28f09986cdb8c562aedfc9deae7b0369214ebc05
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277566"
---
# <a name="performance-recommendations-for-unity"></a>對 Unity 的效能建議

本文是以[混合實境效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unity 引擎環境的特定學習。

## <a name="use-recommended-unity-project-settings"></a>使用建議的 Unity 專案設定

將 Unity 中的混合實境應用程式效能最佳化時，最重要的第一個步驟是確定您已使用 [Unity 的建議環境設定](recommended-settings-for-unity.md)。 該文章包含的內容具有一些最重要的場景設定，適用於建立高效能的混合實境應用程式。 其中一些建議的設定也會反白顯示，如下所示。

## <a name="how-to-profile-with-unity"></a>如何使用 Unity 進行分析

Unity 提供內建的 **[Unity 分析工具](https://docs.unity3d.com/Manual/Profiler.html)** ，這是一項絕佳資源，可讓您針對特定應用程式收集寶貴的效能深入解析。 雖然使用者可以在編輯器中執行分析工具，但這些計量並不代表真正的執行時間環境，因此應謹慎使用這些結果。 當您在裝置上執行應用程式時，建議從遠端分析應用程式，以取得最精確且可採取動作的深入解析。 此外，也可使用 Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)，這個工具非常強大且深入解析。

Unity 提供的絕佳文件：
1) 如何從遠端將 [Unity 分析工具連線到 UWP 應用程式](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何使用 Unity 分析工具有效率地[診斷效能問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 當 Unity 分析工具已連線並新增 GPU 分析工具之後 (請參閱右上角的「新增分析工具」  )，使用者可以在分析工具的中間查看 CPU 與 GPU 分別花費了多少時間。 這可讓開發人員在其應用程式為 CPU 或 GPU 限定時，取得快速近似值。
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 效能建議

以下內容涵蓋更深入的效能實務，特別將目標放在 Unity 與 C# 開發。

#### <a name="cache-references"></a>快取參考

最佳做法是在初始化時快取所有相關元件和 GameObject 的參考。 這是因為相對於儲存指標的記憶體成本，重複的函式呼叫 (例如 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* ) 會大幅提高成本。 這也適用於經常使用的 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。 *Camera.main* 只會使用底下的 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，以高成本的方式搜尋場景圖形中含有 *"MainCamera"* 標記的相機物件。

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
> 避免 GetComponent(字串) <br/>
> 使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 時，有少數不同的多載。 請務必一律使用以類型為基礎的實作，而不是使用以字串為基礎的搜尋多載。 在場景中依字串搜尋會比依類型搜尋昂貴許多。 <br/>
> (良好) Component GetComponent(輸入類型) <br/>
> (良好) T GetComponent\<T>() <br/>
> (不良) Component GetComponent(字串)> <br/>

#### <a name="avoid-expensive-operations"></a>避免高成本的作業

1) **避免使用 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    雖然 LINQ 可能會非常簡潔且易於讀寫，但相較於手動撰寫演算法，通常需要更多的計算以及更多的記憶體配置。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **通用 Unity API**

    某些 Unity API 雖然很有用，但執行的成本可能很高。 其中大部分牽涉到在整個場景圖形中搜尋一些相符的 Gameobject 清單。 這些作業通常可加以避免，方法是快取參考或針對有問題的 GameObject 實作管理員元件，以便在執行時間追蹤參考。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> 應不計代價消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 。 這些函式可能會比直接函式呼叫慢大約 1000 倍。

3) **注意 Box 處理**

    [Box 處理](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 語言和執行時間的核心概念。 這是將實值類型變數 (例如 char、int、bool 等) 包裝成參考類型變數的程序。 當實值類型變數為 "boxed" 時，會包裝在儲存於受管理堆積上的 System.Object 中。 因此，系統會配置記憶體，且最終在處置時必須由記憶體回收行程處理。 這些配置和取消配置會產生效能成本，且在許多情況下並不需要，或是可以輕鬆地以較不昂貴的替代方案來取代。

    開發中最常見的 Box 處理形式之一，是使用[可為 Null 的實值類型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。 通常會想要能夠針對函式中的實值類型傳回 null，特別是當作業嘗試取得值時，可能會失敗。 這種方法的潛在問題，是現在會在堆積上進行配置，因此需要在稍後進行記憶體回收行程。

    **C# 中的 Box 處理範例**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **透過可為 Null 的實值類型進行有問題 Box 處理的範例**

    此程式碼會示範一個可在 Unity 專案中建立的虛擬粒子類別。 呼叫 `TryGetSpeed()` 將會導致堆積上的物件配置，而這將需要在稍後的時間點進行記憶體回收行程。 這個範例特別有問題，因為場景中可能有超過 1000 個以上的粒子，而每個粒子都被要求其目前的速度。 因此，1000 多個物件會受到配置，因而每個畫面格都會解除配置，這會大幅降低效能。 重新撰寫函式以傳回負數值 (例如 -1) 來表示失敗則可避免這個問題，並將記憶體保留在堆疊上。

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

任何重複的 Unity 回呼函式 (亦即 Update)，每秒和/或每個畫面格會執行許多次，都應該非常小心地撰寫。 在此，任何高成本的作業都會對效能產生巨大且一致的影響。

1) **空白的回呼函式**

    雖然在您的應用程式中保留下列程式碼可能看似無害，特別是因為每個 Unity 指令碼都會使用此程式碼區塊自動初始化，但這些空白回呼實際上可能會非常昂貴。 Unity 會在未受管理/受管理程式碼界限 (在 UnityEngine 程式碼與您的應用程式程式碼) 之間來回操作。 即使沒有要執行的內容，透過此橋接器切換內容的成本也相當高。 如果您應用程式的 100 多個 GameObject 具有包含空白重複 Unity 回呼的元件，這會變得特別有問題。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() 是這個效能問題最常見的表現，但其他重複的 Unity 回呼 (例如下列情況) 可能會同樣不良 (若非更差狀況)：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等等。 

2) **偏好每個畫面格執行一次的作業**

    下列 Unity API 是許多全像攝影應用程式的常見作業。 雖然不一定能夠這麼做，但這些函式的結果通常可計算一次，且結果會在指定畫面格的整個應用程式中重複使用。

    a) 一般而言，最好具有專用的單一類別或服務來處理場景中的注視 Raycast，然後在所有其他場景元件中重複使用這個結果，而不是每個元件都進行重複且基本上都相同的 Raycast 作業。 當然，有些應用程式可能需要不同來源，或是針對不同 [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html) 的 Raycast。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) 避免重複 Unity 回呼 (例如 Update()) 中的 GetComponent() 作業，方法是在 Start() 或 Awake() 中[快取參考](#cache-references)

        UnityEngine.Object.GetComponent()

    c) 最佳做法是在初始化時將所有物件具現化 (若可能)，並使用[物件集區](#object-pooling)，以在應用程式的整個執行時間回收並重複使用 GameObject

        UnityEngine.Object.Instantiate()

3) **避免介面和虛擬結構**

    透過介面與直接物件來叫用函式呼叫或呼叫虛擬函式，通常比使用直接結構或直接函式呼叫的成本更高。 如果虛擬函式或介面不是必要的，則應該將其移除。 不過，如果利用這些方法可簡化開發共同作業、程式碼可讀性和程式碼維護性，那麼這些方法的效能衝擊通常值得取捨。

    一般來說，建議不要將欄位和函式標示為虛擬，除非有清楚的預期需要覆寫這個成員。 對於在每個畫面格上呼叫多次的高頻率程式碼路徑，或甚至是每個畫面格呼叫一次 (例如 `UpdateUI()` 方法)，都應該特別小心。

4) **避免以傳值方式傳遞結構**

    不同於類別，結構是實值類型，而當直接傳遞至函式時，會將其內容複製到新建立的實例。 此複本會增加 CPU 成本，以及堆疊上的額外記憶體。 針對小型結構，效果通常非常小，因此可接受。 不過，對於每個畫面格重複叫用的函式，以及接受大型結構的函式，如果可能，請將函式定義修改為以傳址方式傳遞。 [請於此處深入了解](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>其他

1) **物理特性**

    a) 一般而言，改善物理特性最簡單的方式，是限制花費在「物理特性」上的時間量，或每秒的反覆運算次數。 當然，這會降低模擬準確度。 請參閱 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)

    b) Unity 中的碰撞器類型具有廣泛不同的效能特性。 下列順序從左至右列出最高效能的碰撞器到最低效能的碰撞器。 請務必避免網格碰撞器，這比基本碰撞器的成本高出許多。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    如需詳細資訊，請參閱 [Unity 物理特性最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)

2) **動畫**

    停用閒置動畫，方法是停用 Animator 元件 (停用遊戲物件不會有相同的效果)。 避免設計出 Animator 所在迴圈將值設定為相同內容的模式。 這項技術會有相當大的負擔，對應用程式則沒有任何影響。 [請於此處深入了解。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雜演算法**

    如果您的應用程式是使用複雜演算法，例如反向運動、路徑尋找等等，請試著尋找較簡單的方法，或調整其效能的相關設定

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU 對 GPU 效能建議

一般來說，CPU 對 GPU 的效能會降至提交到圖形卡的**繪製呼叫**。 為改善效能，必須策略性地將繪製呼叫**降低**或**重建**，以獲得最佳結果。 由於繪製呼叫本身會耗用大量資源，因此減少繪製呼叫會降低所需的整體工作量。 此外，在繪製呼叫之間的狀態變更需要在圖形驅動程式中進行高成本驗證和轉譯步驟，因此，重建應用程式的繪製呼叫來限制狀態變更 (亦即 不同的資料等) 可以提升效能。

Unity 有一篇很棒的文章，可讓您大致瞭解並探討其平台的批次繪製呼叫。
- [Unity 繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>單通道執行個體化轉譯

Unity 中的 [單通道執行個體化轉譯] 可讓您將每個眼球的繪製呼叫降低至一個執行個體化的繪製呼叫。 由於兩個繪製呼叫之間的快取一致性，GPU 上也有一些效能改善。

若要在 Unity 專案中啟用這項功能
1)  開啟 [Player XR 設定]  (移至 [編輯]   > [專案設定]   > [播放器]   > [XR 設定]  )
2) 從 [立體聲轉譯方法]  下拉式功能表中，選取 [單通道執行個體化]  (必須核取 [支援的虛擬實境]  核取方塊)

如需此轉譯方法的詳細資料，請在 Unity 中參閱下列文章。
- [如何使用進階的立體聲轉譯將 AR 和 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單通道執行個體](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果開發人員已經有非針對執行個體撰寫的現有自訂著色器，就會發生單通道執行個體化轉譯的一個常見問題。 啟用這項功能之後，開發人員可能會注意到，有些 GameObject 只會在單一眼球中轉譯。 這是因為相關聯的自訂著色器沒有適當的執行個體屬性。
>
> 如需解決此問題的方法，請參閱 Unity 中的[適用於 HoloLens 的單通道立體聲轉譯](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)

#### <a name="static-batching"></a>靜態批次處理

Unity 能夠批次處理許多靜態物件，以減少對 GPU 的繪製呼叫。 靜態批次處理適用於 Unity 中大部分的[轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)物件，這些物件會 **1) 共用相同的資料** 且 **2) 全部標示為 [靜態] ** (在 Unity 中選取物件，然後按一下偵測器右上方的核取方塊)。 標記為「靜態」  的 GameObject 無法在整個應用程式的執行時間移動。 因此，靜態批次處理可能很容易在 HoloLens 上運用，因為幾乎每個物件都必須放置、移動、調整等等。針對沉浸式頭戴裝置，靜態批次處理可以大幅減少繪製呼叫，因而改善效能。

如需詳細資料，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「靜態批次處理」  。

#### <a name="dynamic-batching"></a>動態批次處理

由於將 HoloLens 開發的物件標示為「靜態」  會有問題，因此動態批次處理可能是彌補這項缺乏功能的絕佳工具。 當然，該功能也適用於沉浸式頭戴裝置。 不過，Unity 中的動態批次處理可能難以啟用，因為 GameObject 必須 **a) 共用相同的資料** 且 **b) 符合一長串的其他條件**。

如需完整清單，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「動態批次處理」  。 最常見的情況是，因為相關聯的網格資料不能超過 300 個頂點，所以 GameObject 會變成無效而無法動態地進行批次處理。

#### <a name="other-techniques"></a>其他技術

只有在多個 GameObject 可以共用相同的資料時，才會進行批次處理。 一般而言，這會因為需要 GameObject 而受到封鎖，使其各自的材質獲得獨特的紋理。 通常會將「紋理」結合成一個大「紋理」，這是一種稱為[紋理圖集](https://en.wikipedia.org/wiki/Texture_atlas)的方法。

此外，通常最好是在可能且合理的情況下，將網格結合成一個 GameObject。 Unity 中的每個轉譯器都會有其相關聯的繪製呼叫，而不會在單一轉譯器下提交合併的網格。

>[!NOTE]
> 在執行時間修改 Renderer.material 的屬性，會建立一份資料複本，因此可能會中斷批次處理。 使用 Renderer.sharedMaterial 來修改 Gameobject 之間的共用材質屬性。

## <a name="gpu-performance-recommendations"></a>GPU 效能建議

深入瞭解如何[將 Unity 中的圖形轉譯進行最佳化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>將深度緩衝區共用進行最佳化

通常建議您啟用 [Player XR 設定]  下的 [深度緩衝區共用]  ，以將[全像投影穩定性](Hologram-stability.md)進行最佳化。 不過，使用此設定來啟用深度延遲階段重新投影時，建議選取 [16 位元深度格式]  ，而不是 [24 位元深度格式]  。 16 位元深度緩衝區會大幅降低與深度緩衝區流量相關聯的頻寬 (和電源)。 這在降低電源和改善效能方面都是一大優勢。 不過，使用「16 位元深度格式」  可能會有兩個負面結果。

**Z 衝突**

降低的深度範圍精確度會使 [z 衝突](https://en.wikipedia.org/wiki/Z-fighting)較可能發生在 16 位元而非 24 位元。 若要避免這些成品，請修改 [Unity 攝影機](https://docs.unity3d.com/Manual/class-Camera.html)的近/遠裁剪平面，以降低精確度。 對於 HoloLens 型應用程式，50m 的遠裁剪平面而非 Unity 預設的 1000m 裁剪平面通常可以排除任何 z 衝突。

**已停用的樣板緩衝區**

當 Unity 建立[具有 16 位元深度的轉譯紋理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)時，並不會建立樣板緩衝區。 根據 Unity 文件選取 24 位元深度格式，將會建立 24 位元的 z 緩衝區，以及 [8 位元樣板緩衝區] (https://docs.unity3d.com/Manual/SL-Stencil.html) (如果裝置適用 32 位元，這通常是 HoloLens 之類的情況)。

### <a name="avoid-full-screen-effects"></a>避免全螢幕效果

在全螢幕上操作的技術可能會相當高成本，因為其大小順序是每個畫面格數百萬個作業。 因此，建議您避免[後置處理效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html) (例如消除鋸齒、綻開等等)。

### <a name="optimal-lighting-settings"></a>最佳光源設定

Unity 中的[即時全域照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供優異的視覺結果，但牽涉到相當高成本的光源計算。 建議您透過 [視窗]   > [轉譯]   > [光源設定]  > 取消核取 [即時全域照明]  ，停用每個 Unity 場景檔案的即時全域照明。

此外，建議停用所有陰影轉換，因為這些也會在 Unity 場景上增加高成本的 GPU 通道。 可針對光源停用陰影，也可以透過 [品質] 設定進行全面性控制。

[編輯]   > [專案設定]  ，然後選取 [品質]  類別 > 針對 UWP 平台，選取 [低品質]  。 使用者也可以只將 [陰影]  屬性設定為 [停用陰影]  。

### <a name="reduce-poly-count"></a>減少多邊形計數

多邊形計數通常會縮減為
1) 從場景移除物件
2) 資產減去，可減少指定網格的多邊形數目
3) 將[詳細資料的層級 (LOD) 系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)實作到您的應用程式中，以相同幾何的較低多邊形版本呈現遙遠的物件

### <a name="understanding-shaders-in-unity"></a>瞭解 Unity 中的著色器

比較效能中著色器的簡單近似值，是識別在執行時間每個執行的平均作業數目。 這可以在 Unity 中輕鬆完成。

1) 選取您的著色器資產或選取材質，然後在偵測器視窗的右上角，選取後接 [選取著色器]  的齒輪圖示

    ![選取 Unity 中的著色器](images/Select-shader-unity.png)
2) 選取著色器資產後，按一下偵測器視窗下的 [編譯並顯示程式碼]  按鈕

    ![在 Unity 中編譯著色器程式碼](images/compile-shader-code-unity.PNG)

3) 編譯之後，在結果中尋找統計資料區段，其中包含頂點和像素著色器的不同作業數目 (注意：像素著色器通常也稱為片段著色器)

    ![Unity 標準著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>最佳化像素著色器

使用上述方法查看編譯的統計資料結果，[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會比 [頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均執行更多作業。 片段著色器 (也稱為像素著色器) 會針對螢幕輸出上的每個像素執行，而頂點著色器只會針對繪製到螢幕的所有網格中每個頂點來執行。 

因此，片段著色器不只會因所有光源計算而比頂點著色器有更多的指示，片段著色器通常還會在較大的資料集上執行。 例如，如果螢幕輸出是 2k 比 2k 影像，則片段著色器可執行 2,000*2,000 = 4,000,000 次。 如果呈現兩眼，這個數字會加倍，因為有兩個畫面。 如果混合實境應用程式有多個通道、全螢幕後置處理效果，或將多個網格轉譯為相同的像素，這個數字就會大幅增加。 

因此，減少片段著色器中的作業數目，通常可以在端點著色器中提供比最佳化更佳的效能提升。

#### <a name="unity-standard-shader-alternatives"></a>Unity 標準著色器作業

您不需要使用以實體為基礎的轉譯 (PBR) 或其他高品質的著色器，而是瞭解如何利用更高的效能及更低成本的著色器。 [混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供已針對混合實境專案進行最佳化的 [MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。

Unity 也提供無光、頂點光、擴散和其他簡化的著色器選項，相較於 Unity 標準著色器，速度大幅提升。 如需詳細資訊，請參閱[內建著色器的用法和效能](https://docs.unity3d.com/Manual/shader-Performance.html)。

#### <a name="shader-preloading"></a>著色器預先載入

使用「著色器預先載入」  和其他訣竅，將[著色器載入時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)進行最佳化。 特別是，著色器預先載入表示您不會因為執行時間著色器編譯而看到任何停頓。

### <a name="limit-overdraw"></a>限制過度繪製

在 Unity 中，使用者可以顯示其場景的過度繪製，方法是切換 [場景視圖]  左上角的 [[繪製模式] 功能表  ](https://docs.unity3d.com/Manual/ViewModes.html)，然後選取 [過度繪製]  。

一般來說，在將物件傳送至 GPU 之前，您可以將這些物件先行剔除，藉以減輕過度繪製。 Unity 提供針對其引擎實作[遮蔽剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的詳細資料。

## <a name="memory-recommendations"></a>記憶體建議

記憶體過度配置及解除配置的作業可能會對您的全像攝影應用程式造成不良的影響，因而導致效能不一致、凍結的畫面格和其他不利的行為。 在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由記憶體回收行程所控制。

#### <a name="garbage-collection"></a>記憶體回收行程

當記憶體回收行程 (GC) 啟動以分析不在執行期間範圍中的物件，且需要釋放其記憶體時，全像攝影應用程式將會遺失處理記憶體回收行程的計算時間，因此可供重複使用。 常數配置和取消配置通常需要更頻繁地執行記憶體回收行程，因而會影響效能和使用者體驗。

Unity 提供了絕佳的頁面，詳細說明記憶體回收行程的運作方式，以及在記憶體管理方面撰寫更有效率程式碼的秘訣。
- [將 Unity 遊戲中的記憶體回收行程進行最佳化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

導致過多記憶體回收行程最常見的做法之一，是不會快取 Unity 開發中元件和類別的參考。 任何參考都應該在 Start() 或 Awake() 期間加以擷取，然後在 Update() 或 LateUpdate() 等函式中重複使用。

其他快速提示：
- 使用 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 類別，在執行時間以動態方式建置複雜字串
- 當您不再需要 Debug.Log() 的呼叫時，請加以移除，因為該函式仍會在應用程式的所有組建版本中執行
- 如果您的全像攝影應用程式通常需要大量的記憶體，請考慮在載入階段 (例如，呈現載入或轉換畫面時) 呼叫 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)

#### <a name="object-pooling"></a>物件集區

物件集區是一種常用的技術，可降低連續配置及取消配置物件的成本。 這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。 物件集區非常適合在應用程式期間有變數存留期的重複使用元件。

- [Unity 中的物件集區教學課程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>啟動效能

您應該考慮使用較小的場景來啟動您的應用程式，然後使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 載入場景的其餘部分。 這可讓您的應用程式盡可能快速地進入互動狀態。 請注意，當新的場景啟動時，可能會有大型的 CPU 尖峰，而且任何轉譯的內容可能會斷斷續續或是停頓。 解決這個情況的方法之一，就是在要載入的場景上，將 AsyncOperation.allowSceneActivation 屬性設為 "false"，等待場景載入，將畫面清除為黑色，然後將其設回 "true"，以完成場景啟用。

請記住，當啟動場景在載入時，會向使用者顯示全像攝影畫面。

## <a name="see-also"></a>另請參閱
- [將 Unity 遊戲中的圖形轉譯進行最佳化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [將 Unity 遊戲中的記憶體回收行程進行最佳化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理特性最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [將指令碼進行最佳化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
