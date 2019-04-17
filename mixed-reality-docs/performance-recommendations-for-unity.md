---
title: Unity 的效能建議
description: 若要改善效能與混合的實境應用程式的 unity 特有秘訣。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形中，cpu、 gpu 轉譯，記憶體回收，hololens
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597050"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="a13de-104">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="a13de-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="a13de-105">這篇文章是根據所述的討論[混合實境的效能建議](understanding-performance-for-mixed-reality.md)但著重於 Unity 引擎環境特有的做法。</span><span class="sxs-lookup"><span data-stu-id="a13de-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="a13de-106">它也是強烈建議開發人員檢閱[環境的建議設定是 Unity 文件](Recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="a13de-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="a13de-107">這篇文章有內容，但是某些最重要的場景設定建置高效能 Mixed Reality 應用程式的相關事宜。</span><span class="sxs-lookup"><span data-stu-id="a13de-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="a13de-108">其中某些建議設定會反白顯示下面也。</span><span class="sxs-lookup"><span data-stu-id="a13de-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="a13de-109">如何使用 Unity 設定檔</span><span class="sxs-lookup"><span data-stu-id="a13de-109">How to profile with Unity</span></span>

<span data-ttu-id="a13de-110">Unity 提供**[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 內建，也就是絕佳的資源來收集特定應用程式的重要效能深入解析。</span><span class="sxs-lookup"><span data-stu-id="a13de-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="a13de-111">雖然可以執行程式碼剖析工具編輯器內，這些度量不代表，則為 true 的執行階段環境，因此，從這個結果應小心。</span><span class="sxs-lookup"><span data-stu-id="a13de-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="a13de-112">建議從遠端設定檔應用程式時最精確且可付諸行動的深入解析的裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="a13de-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="a13de-113">此外，Unity[框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)也是非常強大和深入解析 」 工具使用。</span><span class="sxs-lookup"><span data-stu-id="a13de-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="a13de-114">Unity 提供絕佳的文件：</span><span class="sxs-lookup"><span data-stu-id="a13de-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="a13de-115">如何連接[UWP 應用程式的 Unity 分析工具從遠端](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="a13de-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="a13de-116">如何有效地[診斷效能問題與 Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="a13de-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="a13de-117">連線的 Unity Profiler 和加入 GPU 分析工具 (請參閱*新增 Profiler*在右上角)，可以看到多少時間花在 CPU 和 GPU 上分別中間程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="a13de-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="a13de-118">這可讓開發人員取得快速的近似值，它們的應用程式是否 CPU 或 GPU 繫結。</span><span class="sxs-lookup"><span data-stu-id="a13de-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="a13de-120">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="a13de-120">CPU performance recommendations</span></span>

<span data-ttu-id="a13de-121">以下內容涵蓋更多深入的效能做法，特別是針對 Unity （& s)C#開發。</span><span class="sxs-lookup"><span data-stu-id="a13de-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="a13de-122">快取的參考</span><span class="sxs-lookup"><span data-stu-id="a13de-122">Cache references</span></span>

<span data-ttu-id="a13de-123">它是最佳的作法，以在初始化的快取參考所有相關的元件和 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="a13de-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="a13de-124">這是因為這類重複函式呼叫*[GetComponent\<T > （)](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 成本遠相對於記憶體的指標儲存成本。</span><span class="sxs-lookup"><span data-stu-id="a13de-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="a13de-125">這也適用於以非常中，定期[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。</span><span class="sxs-lookup"><span data-stu-id="a13de-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="a13de-126">*Camera.main*實際上只會使用*[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 低廉中搜尋您的場景圖形具有相機物件底下 *"MainCamera 」* 標記。</span><span class="sxs-lookup"><span data-stu-id="a13de-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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

>[!NOTE] <span data-ttu-id="a13de-127">Avoid GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="a13de-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="a13de-128">使用時 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*，有少數幾個不同的多載。</span><span class="sxs-lookup"><span data-stu-id="a13de-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="a13de-129">請務必一律使用基礎的型別實作，而永遠不會以字串為基礎的搜尋多載。</span><span class="sxs-lookup"><span data-stu-id="a13de-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="a13de-130">根據在場景中的字串會大幅的成本高於搜尋型別。</span><span class="sxs-lookup"><span data-stu-id="a13de-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="a13de-131">（好）元件 GetComponent (類型 type)</span><span class="sxs-lookup"><span data-stu-id="a13de-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="a13de-132">（好）T GetComponent\<T > （)</span><span class="sxs-lookup"><span data-stu-id="a13de-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="a13de-133">（錯誤）元件 GetComponent(string) ></span><span class="sxs-lookup"><span data-stu-id="a13de-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="a13de-134">避免耗費資源的作業</span><span class="sxs-lookup"><span data-stu-id="a13de-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="a13de-135">**請避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="a13de-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="a13de-136">雖然非常簡潔又方便讀取和寫入，可使用 LINQ，通常需要更多計算和特別更多的記憶體配置比手動寫出的演算法。</span><span class="sxs-lookup"><span data-stu-id="a13de-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="a13de-137">**常見的 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="a13de-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="a13de-138">特定的 Unity Api，雖然很實用，可以是執行代價很高。</span><span class="sxs-lookup"><span data-stu-id="a13de-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="a13de-139">其中大部分涉及搜尋整個場景圖形的一些符合 Gameobject 的清單。</span><span class="sxs-lookup"><span data-stu-id="a13de-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="a13de-140">這些作業通常可以避免快取的參考，或實作管理員元件的問題來追蹤在執行階段參考 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="a13de-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="a13de-141">*[Sendmessage （)](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 並*[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 應該全力排除。</span><span class="sxs-lookup"><span data-stu-id="a13de-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="a13de-142">這些函式可以是大約 1000 x 低於直接函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="a13de-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="a13de-143">**請注意 boxing**</span><span class="sxs-lookup"><span data-stu-id="a13de-143">**Beware of boxing**</span></span>

    <span data-ttu-id="a13de-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是的核心概念C#語言和執行階段。</span><span class="sxs-lookup"><span data-stu-id="a13de-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="a13de-145">它會為參考型別變數包裝實值類型的變數，例如 char、 int、 bool 等程序。</span><span class="sxs-lookup"><span data-stu-id="a13de-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="a13de-146">當實值類型的變數為"boxed，時"會將它包裝在 System.Object 儲存在 managed 堆積上。</span><span class="sxs-lookup"><span data-stu-id="a13de-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="a13de-147">因此，配置的記憶體和最終處置時，才必須處理必要的記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="a13de-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="a13de-148">這些配置和解除配置會產生效能成本和在許多情況下是不必要或可以輕鬆地取代成本較低的替代方案。</span><span class="sxs-lookup"><span data-stu-id="a13de-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

#### <a name="repeating-code-paths"></a><span data-ttu-id="a13de-149">重複的程式碼路徑</span><span class="sxs-lookup"><span data-stu-id="a13de-149">Repeating code paths</span></span>

<span data-ttu-id="a13de-150">任何重複的 Unity 回呼函數 （也就是</span><span class="sxs-lookup"><span data-stu-id="a13de-150">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="a13de-151">更新），每秒的次數執行及/或應該非常小心地寫入畫面格。</span><span class="sxs-lookup"><span data-stu-id="a13de-151">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="a13de-152">任何耗費資源的作業會對效能有很大且一致的影響。</span><span class="sxs-lookup"><span data-stu-id="a13de-152">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="a13de-153">**空白的回呼函式**</span><span class="sxs-lookup"><span data-stu-id="a13de-153">**Empty callback functions**</span></span>

    <span data-ttu-id="a13de-154">下列程式碼看似無害將保留在您的應用程式，特別是因為每個 Unity 指令碼自動初始化此程式碼區塊時，雖然這些空白回呼可以實際成為非常耗費資源。</span><span class="sxs-lookup"><span data-stu-id="a13de-154">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="a13de-155">Unity 來回運作 UnityEngine 的程式碼和應用程式程式碼之間的 unmanaged/managed 程式碼界限。</span><span class="sxs-lookup"><span data-stu-id="a13de-155">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="a13de-156">切換此橋接器的內容就非常高昂，即使沒有任何項目執行。</span><span class="sxs-lookup"><span data-stu-id="a13de-156">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="a13de-157">這會成為您的應用程式是否有空白的重複 Unity 回呼的元件的 Gameobject 可擴充的特別有問題。</span><span class="sxs-lookup"><span data-stu-id="a13de-157">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="a13de-158">Update （） 是此效能問題的最常見的現象，但其他重複的 Unity 回呼，如下所示可以同樣好到哪裡去如果不更差：FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span><span class="sxs-lookup"><span data-stu-id="a13de-158">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="a13de-159">**偏好執行一次作業每個畫面**</span><span class="sxs-lookup"><span data-stu-id="a13de-159">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="a13de-160">下列的 Unity Api 是許多全像攝影版的應用程式的一般作業。</span><span class="sxs-lookup"><span data-stu-id="a13de-160">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="a13de-161">雖然不一定可行，這些函式的結果可以非常頻繁計算一次和結果重新利用指定的範圍內的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a13de-161">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="a13de-162">a） 通常最好有專用的單一類別或服務來處理您的視線 Raycast 場景，並接著在所有其他場景的元件，而不是由每個進行重複和基本上相同 Raycast 作業中重複使用此結果元件。</span><span class="sxs-lookup"><span data-stu-id="a13de-162">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="a13de-163">當然，有些應用程式可能需要來自不同的來源，或針對不同的 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。</span><span class="sxs-lookup"><span data-stu-id="a13de-163">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="a13de-164">b） 避免 GetComponent() 作業中重複的 Unity 回呼，例如 update （） 所[快取參考](#cache-references)start （） 或 Awake() 中</span><span class="sxs-lookup"><span data-stu-id="a13de-164">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="a13de-165">c） 是很好的作法，所有物件，可能的話，請在初始設定和使用具現都化[物件集區](#object-pooling)回收，並重複使用整個應用程式的執行階段的 Gameobject</span><span class="sxs-lookup"><span data-stu-id="a13de-165">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="a13de-166">**避免介面和虛擬的建構**</span><span class="sxs-lookup"><span data-stu-id="a13de-166">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="a13de-167">叫用函式呼叫，透過介面與直接物件或呼叫虛擬函式通常可以比使用直接建構或直接函式呼叫昂貴許多。</span><span class="sxs-lookup"><span data-stu-id="a13de-167">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="a13de-168">如果介面的虛擬函式是不必要的則應予以移除。</span><span class="sxs-lookup"><span data-stu-id="a13de-168">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="a13de-169">不過，效能的衝擊針對這些方法通常是值得取捨如果利用它們可簡化開發共同作業、 程式碼的可讀性及程式碼維護性。</span><span class="sxs-lookup"><span data-stu-id="a13de-169">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span> 

4) <span data-ttu-id="a13de-170">**值，以避免傳遞結構**</span><span class="sxs-lookup"><span data-stu-id="a13de-170">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="a13de-171">不同於類別，結構是實值型別，並直接傳遞至函式，當其內容複製到新建立的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a13de-171">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="a13de-172">此複本會將 CPU 成本以及其他在堆疊上的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a13de-172">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="a13de-173">對於小型結構，結果會是通常很少，因此可接受。</span><span class="sxs-lookup"><span data-stu-id="a13de-173">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="a13de-174">不過，針對函式重複叫用每個畫面，以及採取大型結構的函式，如果可能的話修改以傳址方式傳遞的函式定義。</span><span class="sxs-lookup"><span data-stu-id="a13de-174">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="a13de-175">進一步了解</span><span class="sxs-lookup"><span data-stu-id="a13de-175">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="a13de-176">其他</span><span class="sxs-lookup"><span data-stu-id="a13de-176">Miscellaneous</span></span>

1) <span data-ttu-id="a13de-177">**物理**</span><span class="sxs-lookup"><span data-stu-id="a13de-177">**Physics**</span></span>

    <span data-ttu-id="a13de-178">a） 一般，以改善物理的最簡單方式是時間的限制物理或每秒的次數所花費量。</span><span class="sxs-lookup"><span data-stu-id="a13de-178">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="a13de-179">當然，這會減少模擬精確度。</span><span class="sxs-lookup"><span data-stu-id="a13de-179">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="a13de-180">請參閱[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity 中</span><span class="sxs-lookup"><span data-stu-id="a13de-180">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="a13de-181">在 Unity colliders b） 的類型有差異很大的效能特性。</span><span class="sxs-lookup"><span data-stu-id="a13de-181">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="a13de-182">下列順序列出從左到右以最少的高效能 colliders 大部分高效能 colliders。</span><span class="sxs-lookup"><span data-stu-id="a13de-182">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="a13de-183">它是最重要，以避免 Mesh Colliders 也就是比基本 colliders 更加昂貴。</span><span class="sxs-lookup"><span data-stu-id="a13de-183">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="a13de-184">請參閱[Unity 物理最佳作法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)如需詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a13de-184">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="a13de-185">**動畫**</span><span class="sxs-lookup"><span data-stu-id="a13de-185">**Animations**</span></span>

    <span data-ttu-id="a13de-186">藉由停用動畫元件停用閒置的動畫 （停用遊戲物件將不會有相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="a13de-186">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="a13de-187">請避免設計模式的動畫會位於迴圈，將值設定為相同的動作。</span><span class="sxs-lookup"><span data-stu-id="a13de-187">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="a13de-188">沒有針對此技術，不會影響應用程式使用大量的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="a13de-188">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="a13de-189">深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="a13de-189">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="a13de-190">**複雜的演算法**</span><span class="sxs-lookup"><span data-stu-id="a13de-190">**Complex algorithms**</span></span>

    <span data-ttu-id="a13de-191">如果您的應用程式使用反向運動、 路徑尋找等複雜的演算法，看起來以尋找更簡單的方法，或調整其效能的相關設定</span><span class="sxs-lookup"><span data-stu-id="a13de-191">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="a13de-192">CPU-GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="a13de-192">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="a13de-193">一般而言，CPU-GPU 效能來到下移**繪製呼叫**送出至圖形卡。</span><span class="sxs-lookup"><span data-stu-id="a13de-193">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="a13de-194">若要改善效能，繪製呼叫必須是策略性**a） 減少**或**b） 重新編排**為獲得最佳結果。</span><span class="sxs-lookup"><span data-stu-id="a13de-194">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="a13de-195">由於繪製呼叫本身是需要大量資源，減少它們將會減少所需的整體工作。</span><span class="sxs-lookup"><span data-stu-id="a13de-195">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="a13de-196">此外，狀態 繪製呼叫之間的變更需要高成本的驗證和轉譯圖形驅動程式中的步驟，因此，重組您的應用程式繪製呼叫，以限制狀態變更 （亦即</span><span class="sxs-lookup"><span data-stu-id="a13de-196">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="a13de-197">不同的資料等），可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="a13de-197">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="a13de-198">Unity 有一篇好文章，提供概觀，並探討其平台的繪製呼叫的批次。</span><span class="sxs-lookup"><span data-stu-id="a13de-198">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="a13de-199">Unity 繪製呼叫批次</span><span class="sxs-lookup"><span data-stu-id="a13de-199">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="a13de-200">單一行程的執行個體的轉譯</span><span class="sxs-lookup"><span data-stu-id="a13de-200">Single pass instanced rendering</span></span>

<span data-ttu-id="a13de-201">在 Unity 中的單一階段 Instanced 呈現可讓您降低下一個執行個體的繪製呼叫眼睛的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="a13de-201">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="a13de-202">因為兩個繪製呼叫之間的快取一致性，另外還有一些效能改進，以及在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="a13de-202">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="a13de-203">若要啟用這項功能在您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="a13de-203">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="a13de-204">開啟**Player XR 設定**(前往**編輯** > **專案設定** > **Player**  > **XR 設定**)</span><span class="sxs-lookup"><span data-stu-id="a13de-204">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="a13de-205">選取 **執行個體的單一傳遞**從**立體轉譯方法**下拉式選單 (**虛擬實境支援**必須選取核取方塊)</span><span class="sxs-lookup"><span data-stu-id="a13de-205">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="a13de-206">如需詳細資訊，此轉譯方法，從 Unity 閱讀下列文章。</span><span class="sxs-lookup"><span data-stu-id="a13de-206">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="a13de-207">如何使用進階的立體聲呈現的 AR 及 VR 效能最大化</span><span class="sxs-lookup"><span data-stu-id="a13de-207">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="a13de-208">單一行程的執行個體</span><span class="sxs-lookup"><span data-stu-id="a13de-208">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="a13de-209">如果開發人員已經不是針對撰寫的現有自訂著色器，就會發生一個常見的問題，使用單一傳遞執行個體轉譯執行個體。</span><span class="sxs-lookup"><span data-stu-id="a13de-209">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="a13de-210">之後啟用此功能，開發人員可能會注意到某些 Gameobject 唯一呈現，一眼中。</span><span class="sxs-lookup"><span data-stu-id="a13de-210">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="a13de-211">這是因為相關聯的自訂著色器沒有適當的屬性執行個體。</span><span class="sxs-lookup"><span data-stu-id="a13de-211">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="a13de-212">請參閱[單一傳遞是立體聲呈現 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)從 Unity 如何解決這個問題</span><span class="sxs-lookup"><span data-stu-id="a13de-212">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="a13de-213">靜態批次處理</span><span class="sxs-lookup"><span data-stu-id="a13de-213">Static batching</span></span>

<span data-ttu-id="a13de-214">Unity 是能夠減少 gpu 的繪製呼叫的許多靜態物件的批次。</span><span class="sxs-lookup"><span data-stu-id="a13de-214">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="a13de-215">靜態批次處理適用於大部分[轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)Unity 中的物件， **1） 共用相同的內容**並**2） 可以為所有標示\*靜態**\* (在 Unity 中選取物件，然後按一下右上角的核取方塊的 偵測器的權限)。</span><span class="sxs-lookup"><span data-stu-id="a13de-215">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="a13de-216">Gameobject 標示*靜態*無法移動整個應用程式的執行階段。</span><span class="sxs-lookup"><span data-stu-id="a13de-216">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="a13de-217">因此，靜態批次處理很難在何處放置時，移動、 縮放等幾乎每個物件的 HoloLens 上運用。沈浸式耳機，靜態批次處理可以大幅降低繪製呼叫並提升效能。</span><span class="sxs-lookup"><span data-stu-id="a13de-217">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="a13de-218">讀取*靜態批次處理*下方[繪製呼叫批次中 Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a13de-218">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="a13de-219">動態批次處理</span><span class="sxs-lookup"><span data-stu-id="a13de-219">Dynamic batching</span></span>

<span data-ttu-id="a13de-220">因為它是將物件標示為有問題*靜態*HoloLens 開發動態批次處理可以是很棒的工具，可彌補這一點缺少功能。</span><span class="sxs-lookup"><span data-stu-id="a13de-220">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="a13de-221">當然，它是可以也是在沉浸式耳機也很有用。</span><span class="sxs-lookup"><span data-stu-id="a13de-221">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="a13de-222">在 Unity 中的動態批次處理很難透過啟用，因為必須 Gameobject **a） 共用相同的內容**並**b） 符合一長串的其他準則**。</span><span class="sxs-lookup"><span data-stu-id="a13de-222">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="a13de-223">讀取*動態批次處理*下方[繪製呼叫批次中 Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)的完整清單。</span><span class="sxs-lookup"><span data-stu-id="a13de-223">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="a13de-224">大多數情況下，Gameobject 變成無效，因為相關聯的網狀結構資料可能會不超過 300 個頂點動態批次處理。</span><span class="sxs-lookup"><span data-stu-id="a13de-224">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="a13de-225">其他技術</span><span class="sxs-lookup"><span data-stu-id="a13de-225">Other techniques</span></span>

<span data-ttu-id="a13de-226">批次只能執行多個 Gameobject 是否能夠共用相同的內容。</span><span class="sxs-lookup"><span data-stu-id="a13de-226">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="a13de-227">通常這將會封鎖 Gameobject 及其各自的資料有唯一的材質的需求。</span><span class="sxs-lookup"><span data-stu-id="a13de-227">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="a13de-228">通常會將紋理組合成一個大型的紋理，方法，也稱為[紋理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)。</span><span class="sxs-lookup"><span data-stu-id="a13de-228">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="a13de-229">此外，它通常最好是結合成一個 GameObject 網格，其中可能與合理。</span><span class="sxs-lookup"><span data-stu-id="a13de-229">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="a13de-230">在 Unity 中的每個轉譯器會將它與提交下一個轉譯器結合的網狀結構的繪製呼叫相關聯。</span><span class="sxs-lookup"><span data-stu-id="a13de-230">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span> 

>[!NOTE]
> <span data-ttu-id="a13de-231">修改的屬性 Renderer.material 在執行階段會建立一份資料，並因此可能會中斷批次。</span><span class="sxs-lookup"><span data-stu-id="a13de-231">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="a13de-232">您可以使用 Renderer.sharedMaterial 共用的 material 屬性來修改整個 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="a13de-232">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="a13de-233">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="a13de-233">GPU performance recommendations</span></span>

<span data-ttu-id="a13de-234">深入了解[最佳化 Unity 中的圖形轉譯](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="a13de-234">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="a13de-235">多邊計數減少</span><span class="sxs-lookup"><span data-stu-id="a13de-235">Reduce poly count</span></span>

<span data-ttu-id="a13de-236">多邊形數目通常被減少</span><span class="sxs-lookup"><span data-stu-id="a13de-236">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="a13de-237">移除場景中的物件</span><span class="sxs-lookup"><span data-stu-id="a13de-237">Removing objects from a scene</span></span>
2) <span data-ttu-id="a13de-238">可減少需要指定網格的多邊形的資產減去</span><span class="sxs-lookup"><span data-stu-id="a13de-238">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="a13de-239">實作[層級的詳細資料 」 (LOD) 系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)到您的應用程式會呈現很遠的位置具有較低多邊形版本的相同 geometry 物件</span><span class="sxs-lookup"><span data-stu-id="a13de-239">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="a13de-240">過度限制</span><span class="sxs-lookup"><span data-stu-id="a13de-240">Limit overdraw</span></span>

<span data-ttu-id="a13de-241">在 Unity 中，一個可以顯示切換其場景，如過度[**繪製模式 功能表**](https://docs.unity3d.com/Manual/ViewModes.html)中的左上角**場景檢視**，然後選取**過度繪製**.</span><span class="sxs-lookup"><span data-stu-id="a13de-241">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="a13de-242">一般而言，過度繪製可減輕剔除事先，再傳送到 GPU 的物件。</span><span class="sxs-lookup"><span data-stu-id="a13de-242">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="a13de-243">Unity 提供詳細資料上實作[閉塞挑選](https://docs.unity3d.com/Manual/OcclusionCulling.html)其引擎。</span><span class="sxs-lookup"><span data-stu-id="a13de-243">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

#### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="a13de-244">了解 Unity 中的著色器</span><span class="sxs-lookup"><span data-stu-id="a13de-244">Understanding shaders in Unity</span></span>

<span data-ttu-id="a13de-245">簡單的概略比較效能的著色器是以識別每個作業的平均數目，在執行階段執行。</span><span class="sxs-lookup"><span data-stu-id="a13de-245">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="a13de-246">這都可以在 Unity 中輕鬆完成。</span><span class="sxs-lookup"><span data-stu-id="a13de-246">This can be done fairly easily in Unity.</span></span>

1) <span data-ttu-id="a13de-247">選取您的著色器資產或選取的資料，然後在右上角的 [偵測器] 視窗，選取齒輪圖示，然後 **"選取著色器 」**</span><span class="sxs-lookup"><span data-stu-id="a13de-247">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![選取 在 Unity 中的 著色器](images/Select-shader-unity.png)
2) <span data-ttu-id="a13de-249">與著色器資產選取的情況下，按一下 **「 編譯和顯示程式碼 」** 偵測器視窗底下的按鈕</span><span class="sxs-lookup"><span data-stu-id="a13de-249">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中的著色器程式碼編譯](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="a13de-251">編譯之後，尋找在結果中的統計資料] 區段具有不同的作業，將 [頂點] 與 [像素著色器的數目 (注意： 像素著色器通常也稱為片段著色器)</span><span class="sxs-lookup"><span data-stu-id="a13de-251">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 標準的著色器作業](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="a13de-253">Unity 標準的著色器的替代方案</span><span class="sxs-lookup"><span data-stu-id="a13de-253">Unity Standard shader alternatives</span></span>

<span data-ttu-id="a13de-254">而不是使用根據實際轉譯 (PBR) 或其他高品質的著色器，查看利用更好的效能和成本較低的著色器。</span><span class="sxs-lookup"><span data-stu-id="a13de-254">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="a13de-255">[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供[標準的著色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader)，已經過最佳化的混合的實境專案。</span><span class="sxs-lookup"><span data-stu-id="a13de-255">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a [standard shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="a13de-256">Unity 也提供光環、 頂點的光源、 擴散，並簡化著色器選項，速度明顯高於標準 Unity 著色器。</span><span class="sxs-lookup"><span data-stu-id="a13de-256">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="a13de-257">請參閱[使用量和效能的內建著色器](https://docs.unity3d.com/Manual/shader-Performance.html)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a13de-257">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="a13de-258">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="a13de-258">Memory recommendations</span></span>

<span data-ttu-id="a13de-259">過多的記憶體配置和解除配置作業可以有負面的影響，在您全像攝影版的應用程式，導致不一致的效能、 凍結的畫面格和其他有害的行為。</span><span class="sxs-lookup"><span data-stu-id="a13de-259">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="a13de-260">它是特別重要，因為記憶體管理由記憶體回收行程控制在 Unity 中開發時，了解記憶體考量。</span><span class="sxs-lookup"><span data-stu-id="a13de-260">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="a13de-261">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a13de-261">Garbage collection</span></span>

<span data-ttu-id="a13de-262">分析執行期間不再是範圍內的物件，GC 會啟動，而且其記憶體需要釋出，因此它可以成為可供重複使用時，全像攝影版的應用程式將會遺失記憶體回收行程 (GC) 處理計算時間。</span><span class="sxs-lookup"><span data-stu-id="a13de-262">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="a13de-263">常數的配置和取消配置通常需要更頻繁地執行，因此影響效能和使用者體驗的記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="a13de-263">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="a13de-264">Unity 提供一個絕佳的頁面，其中詳細說明記憶體回收行程的運作方式和撰寫更有效率的程式碼來管理記憶體的相關事宜的秘訣。</span><span class="sxs-lookup"><span data-stu-id="a13de-264">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="a13de-265">最佳化記憶體回收中的 Unity 遊戲</span><span class="sxs-lookup"><span data-stu-id="a13de-265">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="a13de-266">其中一個最常見的作法，會導致過多的記憶體回收不會快取元件和 Unity 開發中的類別的參考。</span><span class="sxs-lookup"><span data-stu-id="a13de-266">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="a13de-267">應該 start （） 或 Awake() 期間擷取和更新版本的函式，例如 update （） 或 LateUpdate() 中重複使用的任何參考。</span><span class="sxs-lookup"><span data-stu-id="a13de-267">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="a13de-268">其他的快速提示：</span><span class="sxs-lookup"><span data-stu-id="a13de-268">Other quick tips:</span></span>
- <span data-ttu-id="a13de-269">使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#以動態方式建立複雜的字串，在執行階段類別</span><span class="sxs-lookup"><span data-stu-id="a13de-269">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="a13de-270">移除對 Debug.Log() 不再需要仍在所有的組建版本的應用程式執行時呼叫</span><span class="sxs-lookup"><span data-stu-id="a13de-270">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="a13de-271">如果您全像攝影版的應用程式通常需要大量記憶體，請考慮呼叫[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)期間載入階段，例如呈現載入時或轉換畫面</span><span class="sxs-lookup"><span data-stu-id="a13de-271">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="a13de-272">物件集區</span><span class="sxs-lookup"><span data-stu-id="a13de-272">Object pooling</span></span>

<span data-ttu-id="a13de-273">物件共用便是常用的技巧來減少連續配置的成本和取消配置的物件。</span><span class="sxs-lookup"><span data-stu-id="a13de-273">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="a13de-274">這是所配置的相同物件的大型集區，並重複使用而不斷產生，並終結一段時間的物件不是此集區中的 非作用中、 可用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a13de-274">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="a13de-275">物件集區很適合重複使用變數的存留期期間應用程式的元件。</span><span class="sxs-lookup"><span data-stu-id="a13de-275">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="a13de-276">物件集區在 Unity 中的教學課程</span><span class="sxs-lookup"><span data-stu-id="a13de-276">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="a13de-277">啟動效能</span><span class="sxs-lookup"><span data-stu-id="a13de-277">Startup performance</span></span>

<span data-ttu-id="a13de-278">您應該考慮使用較小的場景，啟動您的應用程式，然後使用*[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 載入場景的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a13de-278">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="a13de-279">這可讓您的應用程式，以前往 盡快互動狀態。</span><span class="sxs-lookup"><span data-stu-id="a13de-279">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="a13de-280">要注意，可能有大量的 CPU 使用量正在啟動新的場景時，與任何呈現的內容可能會斷斷續續或習以為常。</span><span class="sxs-lookup"><span data-stu-id="a13de-280">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="a13de-281">若要解決這個問題的一個方式是設為 false 的 AsyncOperation.allowSceneActivation 屬性上所載入的場景，等到場景方向，以載入，清除 為黑色，畫面，然後設為 true，以完成場景啟用回。</span><span class="sxs-lookup"><span data-stu-id="a13de-281">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="a13de-282">請記住，雖然在載入啟動場景全像攝影版的啟動顯示畫面將顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="a13de-282">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="a13de-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a13de-283">See also</span></span>
- [<span data-ttu-id="a13de-284">最佳化 Unity 遊戲中的圖形轉譯</span><span class="sxs-lookup"><span data-stu-id="a13de-284">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="a13de-285">最佳化記憶體回收中的 Unity 遊戲</span><span class="sxs-lookup"><span data-stu-id="a13de-285">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="a13de-286">[物理最佳作法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="a13de-286">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="a13de-287">[最佳化指令碼 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="a13de-287">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
