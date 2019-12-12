---
title: Unity 的效能建議
description: 使用混合現實應用程式改善效能的 Unity 特有秘訣。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形，cpu，gpu，轉譯，垃圾收集，hololens
ms.openlocfilehash: 6507667904cfa26dfad1ccf1402cc75f14386609
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003197"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="fe2a6-104">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="fe2a6-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="fe2a6-105">本文是以[混合現實的效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重于 Unity 引擎環境的特定學習。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="fe2a6-106">此外，我們也強烈建議開發人員審查[Unity 的建議環境設定一文](Recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="fe2a6-107">本文包含的內容具有一些最重要的場景設定，可用於建立高效能的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-107">This article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="fe2a6-108">其中一些建議的設定也會反白顯示在下方。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-108">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="fe2a6-109">如何使用 Unity 進行分析</span><span class="sxs-lookup"><span data-stu-id="fe2a6-109">How to profile with Unity</span></span>

<span data-ttu-id="fe2a6-110">Unity 提供內建的 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** ，這是為您的特定應用程式收集寶貴效能見解的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="fe2a6-111">雖然可以在編輯器中執行分析工具，但這些計量並不代表真正的執行時間環境，因此應該謹慎使用這項結果。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="fe2a6-112">建議您在裝置上執行時，從遠端分析應用程式，以取得最精確且可採取動作的深入解析。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="fe2a6-113">此外，Unity 的[框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)也是一個非常強大且深入解析的工具，可供您使用。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="fe2a6-114">Unity 提供的絕佳檔：</span><span class="sxs-lookup"><span data-stu-id="fe2a6-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="fe2a6-115">如何[從遠端將 Unity profiler 連線至 UWP 應用程式](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="fe2a6-116">如何[使用 Unity Profiler 有效率地診斷效能問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="fe2a6-117">當 Unity Profiler 已連線，並在新增 GPU 分析工具之後（請參閱右上角的 [*新增 Profiler* ]），可以在分析工具中間分別看到 CPU & GPU 花費了多少時間。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="fe2a6-118">這可讓開發人員在其應用程式為 CPU 或 GPU 界限時取得快速近似值。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="fe2a6-120">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="fe2a6-120">CPU performance recommendations</span></span>

<span data-ttu-id="fe2a6-121">以下內容涵蓋更深入的效能實務，特別是針對 Unity & C#開發的目標。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="fe2a6-122">快取參考</span><span class="sxs-lookup"><span data-stu-id="fe2a6-122">Cache references</span></span>

<span data-ttu-id="fe2a6-123">最佳做法是在初始化時快取所有相關元件和 Gameobject 的參考。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="fe2a6-124">這是因為重複的函式呼叫（例如 *[GetComponent\<t > （））](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 相對於儲存指標的記憶體成本，會大幅提高成本。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="fe2a6-125">這也適用于經常使用的[攝影機。](https://docs.unity3d.com/ScriptReference/Camera-main.html)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-125">This also applies to to the very regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="fe2a6-126">*攝影機*實際上只使用下方的 *[FindGameObjectsWithTag （）](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，越低廉會在場景圖形中搜尋具有 *"MainCamera"* 標記的攝影機物件。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="fe2a6-127">避免 GetComponent （字串）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="fe2a6-128">使用 *[GetComponent （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 時，有少數不同的多載。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="fe2a6-129">請務必一律使用以型別為基礎的實作為，而不是以字串為基礎的搜尋多載。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-129">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="fe2a6-130">在場景中依字串搜尋會比依類型搜尋更為昂貴。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="fe2a6-131">充分元件 GetComponent （類型類型）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="fe2a6-132">充分T GetComponent\<T > （）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="fe2a6-133">形象元件 GetComponent （字串） ></span><span class="sxs-lookup"><span data-stu-id="fe2a6-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="fe2a6-134">避免耗費資源的作業</span><span class="sxs-lookup"><span data-stu-id="fe2a6-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="fe2a6-135">**避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="fe2a6-136">雖然 LINQ 可以非常簡潔且容易讀寫，但通常需要更多的計算，而且比手動撰寫演算法更多的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="fe2a6-137">**通用 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="fe2a6-138">某些 Unity Api 雖然很有用，但執行的成本可能很高。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="fe2a6-139">其中大部分牽涉到搜尋整個場景圖形，以尋找一些相符的 Gameobject 清單。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="fe2a6-140">這些作業通常可以藉由快取參考或針對有問題的 Gameobject 執行管理員元件來避免，以便在執行時間追蹤參考。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="fe2a6-141">*[SendMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 應會以所有成本排除。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="fe2a6-142">這些函數的順序可能會比直接函式呼叫的1000x 慢。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="fe2a6-143">**注意裝箱**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-143">**Beware of boxing**</span></span>

    <span data-ttu-id="fe2a6-144">「[裝箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)」是C#語言和執行時間的核心概念。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="fe2a6-145">這是將實數值型別變數（例如 char、int、bool 等）包裝成參考型別變數的程式。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="fe2a6-146">當實值型別變數是「已裝箱」時，它會包裝在儲存在 managed 堆積上的 System.object 中。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="fe2a6-147">因此，記憶體會被配置，而最終處置必須由垃圾收集行程處理。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="fe2a6-148">這些配置和取消配置會產生效能成本，而且在許多情況下都不需要，也可以輕鬆地以較不昂貴的替代方案來取代。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="fe2a6-149">開發的其中一個最常見的裝箱形式是使用[可為 null 的實數值型別](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-149">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="fe2a6-150">通常會想要能夠針對函式中的實值型別傳回 null，特別是當作業嘗試取得值時，可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-150">It is common to want to be able to return null for a value type in a function, especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="fe2a6-151">這種方法的潛在問題是，配置現在會在堆積上進行，因此需要在稍後進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-151">The potential problem with this approach is that allocation now occurs on the heap and consequently needs to be garbage collected later.</span></span>

    <span data-ttu-id="fe2a6-152">**中的裝箱範例C#**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-152">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="fe2a6-153">**透過可為 null 的實數值型別進行有問題之裝箱的範例**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-153">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="fe2a6-154">此程式碼示範一個可在 Unity 專案中建立的虛擬物件類別。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-154">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="fe2a6-155">`TryGetSpeed()` 的呼叫將會導致堆積上的物件配置，而這將需要在稍後的時間點進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-155">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="fe2a6-156">這個範例特別有問題，因為場景中可能有超過1000個以上的粒子，而每個都被要求其目前速度。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-156">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="fe2a6-157">因此，1000個物件會被配置，因而解除配置每個畫面格，這會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-157">Thus, 1000's of objects would be allocated and consequently de-allocated every frame, which would greatly diminish performance.</span></span> <span data-ttu-id="fe2a6-158">重新撰寫函式以傳回負數值（例如-1）來表示失敗會避免這個問題，並將記憶體保留在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-158">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="fe2a6-159">重複的程式碼路徑</span><span class="sxs-lookup"><span data-stu-id="fe2a6-159">Repeating code paths</span></span>

<span data-ttu-id="fe2a6-160">任何重複的 Unity 回呼函數（亦即</span><span class="sxs-lookup"><span data-stu-id="fe2a6-160">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="fe2a6-161">Update），每秒執行的次數和/或框架應該非常小心地撰寫。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-161">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="fe2a6-162">在此，任何耗費資源的作業都會對效能產生巨大且一致的影響。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-162">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="fe2a6-163">**空白的回呼函數**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-163">**Empty callback functions**</span></span>

    <span data-ttu-id="fe2a6-164">雖然下列程式碼在您的應用程式中可能看似無害，特別是因為每個 Unity 腳本都會使用此程式碼區塊自動初始化，所以這些空白回呼實際上可能會變得非常昂貴。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-164">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="fe2a6-165">Unity 會在非受控/managed 程式碼界限之間來回操作，在 UnityEngine 程式碼與您的應用程式程式碼之間。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-165">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="fe2a6-166">即使沒有要執行的內容，透過此橋接器的內容切換也相當耗費資源。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-166">Context switching over this bridge is fairly expensive, even if there is nothing to execute.</span></span> <span data-ttu-id="fe2a6-167">如果您的應用程式具有具有空白重複 Unity 回呼之元件的 100 Gameobject，這會變得特別有問題。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-167">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="fe2a6-168">Update （）是此效能問題最常見的表現，但其他重複的 Unity 回呼（例如下列情況）可能會同樣不良，如果不糟： FixedUpdate （）、LateUpdate （）、OnPostRender、OnPreRender （）、OnRenderImage （）等等。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-168">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="fe2a6-169">**針對每個框架執行一次的作業**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-169">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="fe2a6-170">下列 Unity Api 是許多全像攝影應用程式的常見作業。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-170">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="fe2a6-171">雖然不一定能夠這麼做，但這些函式的結果通常會計算一次，並在整個應用程式中針對指定的框架重複使用結果。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-171">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="fe2a6-172">答）通常最好具有專用的單一類別或服務來處理場景中的注視 Raycast，然後在所有其他場景元件中重複使用此結果，而不是每個都有重複的 Raycast 作業。成分.</span><span class="sxs-lookup"><span data-stu-id="fe2a6-172">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="fe2a6-173">當然，有些應用程式可能需要從不同的來源或不同的[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)進行 raycasts。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-173">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="fe2a6-174">b）藉由快取開始（）或喚醒（）中的[參考](#cache-references)，避免重複 Unity 回呼（例如 Update （））中的 GetComponent （）作業</span><span class="sxs-lookup"><span data-stu-id="fe2a6-174">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="fe2a6-175">c）在初始化時將所有物件具現化，並在應用程式的整個執行時間使用[物件](#object-pooling)共用來回收並重複使用 gameobject 是很好的作法</span><span class="sxs-lookup"><span data-stu-id="fe2a6-175">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="fe2a6-176">**避免介面和虛擬結構**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-176">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="fe2a6-177">透過介面來叫用函式呼叫與直接物件或呼叫虛擬函式，通常比使用直接的結構或直接函式呼叫更耗費資源。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-177">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="fe2a6-178">如果虛擬函式或介面不是必要的，則應該將它移除。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-178">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="fe2a6-179">不過，這些方法的效能衝擊通常值得取捨，因為利用它們可簡化開發共同作業、程式碼可讀性和程式碼維護性。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-179">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="fe2a6-180">一般來說，建議您不要將欄位和函式標示為虛擬，除非有清楚的預期需要覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-180">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="fe2a6-181">對於在每個畫面上多次呼叫的高頻率程式碼路徑，或甚至是每個畫面格（例如 `UpdateUI()` 方法），應該特別小心一次。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-181">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="fe2a6-182">**避免以傳值方式傳遞結構**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-182">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="fe2a6-183">不同于類別，結構是實數值型別，而當直接傳遞至函式時，會將其內容複寫到新建立的實例。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-183">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="fe2a6-184">此複本會增加 CPU 成本，以及堆疊上的額外記憶體。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-184">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="fe2a6-185">針對小型結構，效果通常非常小，因此可接受。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-185">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="fe2a6-186">不過，對於重複叫用每個框架的函式，以及接受大型結構的函式，如果可能的話，請修改函式定義以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-186">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="fe2a6-187">在這裡深入了解</span><span class="sxs-lookup"><span data-stu-id="fe2a6-187">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="fe2a6-188">其他</span><span class="sxs-lookup"><span data-stu-id="fe2a6-188">Miscellaneous</span></span>

1) <span data-ttu-id="fe2a6-189">**物理**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-189">**Physics**</span></span>

    <span data-ttu-id="fe2a6-190">答）一般而言，改善物理的最簡單方式是限制花費在物理上的時間量，或每秒的反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-190">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="fe2a6-191">當然，這會降低模擬準確度。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-191">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="fe2a6-192">請參閱 Unity 中的[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-192">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="fe2a6-193">b） Unity 中的 colliders 類型具有廣為不同的效能特性。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-193">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="fe2a6-194">下列順序列出從左至右到最低效能 colliders 的最高效能 colliders。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-194">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="fe2a6-195">最重要的是避免網格 Colliders，這比基本 Colliders 高得多。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-195">It is most important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="fe2a6-196">如需詳細資訊，請參閱[Unity 物理最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-196">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="fe2a6-197">**Animaciones**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-197">**Animations**</span></span>

    <span data-ttu-id="fe2a6-198">停用閒置動畫，方法是停用 Animator 元件（停用遊戲物件不會有相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-198">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="fe2a6-199">避免 animator 位於迴圈中的設計模式，將值設定為相同的內容。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-199">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="fe2a6-200">這項技術會有相當大的負擔，對應用程式沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-200">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="fe2a6-201">在這裡深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-201">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="fe2a6-202">**複雜演算法**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-202">**Complex algorithms**</span></span>

    <span data-ttu-id="fe2a6-203">如果您的應用程式使用複雜的演算法，例如反向運動、路徑尋找等等，則尋找尋找較簡單的方法，或調整其效能的相關設定</span><span class="sxs-lookup"><span data-stu-id="fe2a6-203">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="fe2a6-204">CPU 到 GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="fe2a6-204">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="fe2a6-205">一般來說，CPU 到 GPU 的效能會下降到提交給圖形配接器的**繪製呼叫**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-205">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="fe2a6-206">若要改善效能，必須將繪製呼叫視為策略性**的）減少**或**b）** ，以獲得最佳結果。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-206">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="fe2a6-207">由於繪製呼叫本身會耗用大量資源，因此減少它們會降低所需的整體工作量。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-207">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="fe2a6-208">此外，在繪製呼叫之間的狀態變更，在圖形驅動程式中需要昂貴的驗證和轉譯步驟，因此，重建應用程式的繪製呼叫來限制狀態變更（亦即</span><span class="sxs-lookup"><span data-stu-id="fe2a6-208">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="fe2a6-209">不同的材料等）可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-209">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="fe2a6-210">Unity 有一篇很棒的文章，可讓您大致瞭解並探討其平臺的批次處理繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-210">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="fe2a6-211">Unity 繪製呼叫批次處理</span><span class="sxs-lookup"><span data-stu-id="fe2a6-211">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="fe2a6-212">單一傳遞實例轉譯</span><span class="sxs-lookup"><span data-stu-id="fe2a6-212">Single pass instanced rendering</span></span>

<span data-ttu-id="fe2a6-213">Unity 中的單一傳遞實例轉譯可讓您將每個眼睛的繪製呼叫縮小至一個實例繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-213">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="fe2a6-214">由於兩個繪製呼叫之間的快取一致性，因此也會改善 GPU 上的效能。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-214">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="fe2a6-215">若要在 Unity 專案中啟用這項功能</span><span class="sxs-lookup"><span data-stu-id="fe2a6-215">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="fe2a6-216">開啟**播放 XR 設定**（移至 [**編輯**] > **專案設定** > **Player** > [ **XR 設定**]）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-216">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="fe2a6-217">從 [**身歷聲轉譯方法**] 下拉式功能表選取 [**單一傳遞實例**] （必須核取 [**虛擬實境支援**] 核取方塊）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-217">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="fe2a6-218">如需此轉譯方法的詳細資訊，請參閱 Unity 中的下列文章。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-218">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="fe2a6-219">如何使用 advanced 身歷聲轉譯將 AR 和 VR 效能最大化</span><span class="sxs-lookup"><span data-stu-id="fe2a6-219">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="fe2a6-220">單一階段實例</span><span class="sxs-lookup"><span data-stu-id="fe2a6-220">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="fe2a6-221">如果開發人員已經有不為實例撰寫的現有自訂著色器，就會發生單一階段實例轉譯的一個常見問題。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-221">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="fe2a6-222">啟用這項功能之後，開發人員可能會注意到有些 Gameobject 只會以一眼呈現。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-222">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="fe2a6-223">這是因為相關聯的自訂著色器沒有適當的實例屬性。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-223">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="fe2a6-224">如需解決此問題的方式，請參閱從 Unity 的[HoloLens 的單次傳遞身歷聲](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)轉譯</span><span class="sxs-lookup"><span data-stu-id="fe2a6-224">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="fe2a6-225">靜態批次處理</span><span class="sxs-lookup"><span data-stu-id="fe2a6-225">Static batching</span></span>

<span data-ttu-id="fe2a6-226">Unity 能夠批次處理許多靜態物件，以減少對 GPU 的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-226">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="fe2a6-227">靜態批次處理適用于 Unity 中大部分的[轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)物件**1) 共用相同的**資料, **2) 全部標示為\*靜態**\* (在 unity 中選取物件, 然後按一下偵測器右上方的核取方塊)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-227">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="fe2a6-228">標記為*靜態*的 gameobject 無法在整個應用程式的執行時間移動。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-228">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="fe2a6-229">因此，靜態批次處理可能很容易在 HoloLens 上運用，因為幾乎每個物件都必須放置、移動、調整等等。對於沉浸式耳機，靜態批次處理可以大幅減少繪製呼叫，因而改善效能。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-229">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="fe2a6-230">如需詳細資訊，請參閱[Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的*靜態批次處理*。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-230">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="fe2a6-231">動態批次處理</span><span class="sxs-lookup"><span data-stu-id="fe2a6-231">Dynamic batching</span></span>

<span data-ttu-id="fe2a6-232">由於將物件標示為靜態開發的*靜態*有問題，動態批次處理可能是補償這項缺少功能的絕佳工具。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-232">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="fe2a6-233">當然，它也適用于沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-233">Of course, it can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="fe2a6-234">不過，Unity 中的動態批次處理可能很容易啟用，因為 Gameobject 必須**a）共用相同**的資料， **b）符合一長串的其他準則**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-234">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="fe2a6-235">如需完整清單，請閱讀在[Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)底下的*動態批次處理*。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-235">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="fe2a6-236">最常見的情況是，Gameobject 因為相關聯的網格資料不能超過300的頂點而變成無效而無法動態地進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-236">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="fe2a6-237">其他技術</span><span class="sxs-lookup"><span data-stu-id="fe2a6-237">Other techniques</span></span>

<span data-ttu-id="fe2a6-238">只有在多個 Gameobject 可以共用相同的資料時，才會進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-238">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="fe2a6-239">一般而言，這會被封鎖，因為 Gameobject 需要對其各自的材質具有獨特的材質。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-239">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="fe2a6-240">通常會將材質結合成一個大材質，這是一種稱為[材質 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)的方法。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-240">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="fe2a6-241">此外，通常最好是在可能和合理的情況下，將網格結合成一個 GameObject。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-241">Furthermore, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="fe2a6-242">Unity 中的每個轉譯器都會有其相關聯的繪製呼叫，而不會在單一轉譯器下提交合併的網格。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-242">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="fe2a6-243">修改轉譯器的屬性。在執行時間時，會建立一份資料複本，因此可能會中斷批次處理。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-243">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="fe2a6-244">使用轉譯器. sharedMaterial 來修改跨 Gameobject 的共用材質屬性。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-244">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="fe2a6-245">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="fe2a6-245">GPU performance recommendations</span></span>

<span data-ttu-id="fe2a6-246">深入瞭解如何[優化 Unity 中的圖形呈現](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-246">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="fe2a6-247">優化深度緩衝區共用</span><span class="sxs-lookup"><span data-stu-id="fe2a6-247">Optimize depth buffer sharing</span></span>

<span data-ttu-id="fe2a6-248">通常建議您啟用 [**播放程式 XR 設定**] 底下的**深度緩衝區共用**，以優化[全息影像的穩定性](Hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-248">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="fe2a6-249">不過，使用此設定來啟用深度架構的延遲階段 reprojection 時，建議選取 [ **16 位深度格式**]，而不是 [ **24 位深度] 格式**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-249">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="fe2a6-250">16位深度緩衝區會大幅降低與深度緩衝區流量相關聯的頻寬（和電源）。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-250">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="fe2a6-251">這在電源降低和效能改善方面都是一大優勢。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-251">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="fe2a6-252">不過，有兩個可能的負面結果，其方式是使用*16 位深度格式*。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-252">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="fe2a6-253">**Z-對抗**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-253">**Z-Fighting**</span></span>

<span data-ttu-id="fe2a6-254">較低的深度範圍精確度讓[z 對抗](https://en.wikipedia.org/wiki/Z-fighting)比24位更有可能發生在16位的情況下。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-254">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="fe2a6-255">若要避免這些成品，請修改[Unity 攝影機](https://docs.unity3d.com/Manual/class-Camera.html)附近/遠的裁剪平面，以降低精確度。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-255">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="fe2a6-256">對於 HoloLens 型應用程式，50m 的最大裁剪平面，而不是 Unity 預設1000m，通常可以排除任何 z 對抗。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-256">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="fe2a6-257">**已停用樣板緩衝區**</span><span class="sxs-lookup"><span data-stu-id="fe2a6-257">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="fe2a6-258">當 Unity 建立[具有16位深度的呈現材質](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)時，並不會建立樣板緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-258">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="fe2a6-259">根據 Unity 檔選取24位深度格式，將會建立24位的 z 緩衝區，以及 [8 位樣板緩衝區] （ https://docs.unity3d.com/Manual/SL-Stencil.html) （如果32位適用于裝置，這通常是 HoloLens 之類的情況）。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-259">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="fe2a6-260">避免全螢幕效果</span><span class="sxs-lookup"><span data-stu-id="fe2a6-260">Avoid full-screen effects</span></span>

<span data-ttu-id="fe2a6-261">在全螢幕上操作的技術可能會相當耗費資源，因為其大小順序是每個框架的數百萬個作業。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-261">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="fe2a6-262">因此，建議您避免[後續處理的效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)，例如消除鋸齒、bloom 等等。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-262">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="fe2a6-263">最佳光源設定</span><span class="sxs-lookup"><span data-stu-id="fe2a6-263">Optimal lighting settings</span></span>

<span data-ttu-id="fe2a6-264">Unity 中的[即時全域照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供未完成的視覺效果結果，但牽涉到相當昂貴的光源計算。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-264">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="fe2a6-265">建議您透過**Window** \*\* > 轉譯\*\* > **光源設定**，停用每個 Unity 場景檔案的即時全域照明，> 取消核取**即時全域照明**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-265">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="fe2a6-266">此外，建議停用所有陰影轉換，因為這些也會在 Unity 場景上增加昂貴的 GPU 傳遞。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-266">Furthermore, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="fe2a6-267">您可以針對每個光線停用陰影，但也可以透過品質設定來控制全面性地。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-267">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="fe2a6-268">**編輯** > **專案設定**，然後選取 **品質** 類別 > 選取 UWP 平臺的 **低品質**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-268">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="fe2a6-269">您也可以只設定**shadows**屬性來**停用陰影**。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-269">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="fe2a6-270">減少 poly 計數</span><span class="sxs-lookup"><span data-stu-id="fe2a6-270">Reduce poly count</span></span>

<span data-ttu-id="fe2a6-271">多邊形計數通常會縮減為</span><span class="sxs-lookup"><span data-stu-id="fe2a6-271">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="fe2a6-272">從場景移除物件</span><span class="sxs-lookup"><span data-stu-id="fe2a6-272">Removing objects from a scene</span></span>
2) <span data-ttu-id="fe2a6-273">可減少指定網格多邊形數目的資產減去</span><span class="sxs-lookup"><span data-stu-id="fe2a6-273">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="fe2a6-274">在您的應用程式中執行[層級的詳細資料（LOD）系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)，以相同幾何的較低多邊形版本呈現最遠的物件</span><span class="sxs-lookup"><span data-stu-id="fe2a6-274">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="fe2a6-275">瞭解 Unity 中的著色器</span><span class="sxs-lookup"><span data-stu-id="fe2a6-275">Understanding shaders in Unity</span></span>

<span data-ttu-id="fe2a6-276">比較效能中著色器的一個簡單近似值，就是識別每個在執行時間執行的平均作業數目。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-276">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="fe2a6-277">這可以在 Unity 中輕鬆完成。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-277">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="fe2a6-278">選取您的著色器資產或選取材質，然後在 [偵測器] 視窗的右上角，選取齒輪圖示，後面接著 **[選取著色器**]</span><span class="sxs-lookup"><span data-stu-id="fe2a6-278">Select your shader asset or select a material, then in the top right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![選取 Unity 中的著色器](images/Select-shader-unity.png)
2) <span data-ttu-id="fe2a6-280">選取著色器資產後，按一下 [偵測器] 視窗底下的 [**編譯並顯示程式碼**] 按鈕</span><span class="sxs-lookup"><span data-stu-id="fe2a6-280">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中編譯著色器程式碼](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="fe2a6-282">編譯之後，在結果中尋找 [統計資料] 區段，其中包含頂點和圖元著色器的不同作業數目（注意：圖元著色器通常也稱為片段著色器）</span><span class="sxs-lookup"><span data-stu-id="fe2a6-282">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 標準著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="fe2a6-284">優化圖元著色器</span><span class="sxs-lookup"><span data-stu-id="fe2a6-284">Optimize pixel shaders</span></span>

<span data-ttu-id="fe2a6-285">使用上述方法查看已編譯的統計資料結果，[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會比端點[著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)執行更多作業，平均。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-285">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="fe2a6-286">片段著色器（也稱為圖元著色器）會針對螢幕輸出上的每個圖元執行，而頂點著色器只會針對繪製到螢幕的所有網格的每個頂點來執行。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-286">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="fe2a6-287">因此，由於所有光源計算，片段著色器通常會在較大的資料集上執行，因此不只會有比頂點著色器更多的指示。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-287">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="fe2a6-288">例如，如果螢幕輸出是 2k by 2k 影像，則片段著色器可執行 2000 \* 2000 = 4000000 次。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-288">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="fe2a6-289">如果呈現兩眼，這個數位會加倍，因為有兩個畫面。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-289">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="fe2a6-290">如果混合現實應用程式有多個階段、全螢幕後置處理效果，或將多個網格轉譯為相同的圖元，這個數位會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-290">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="fe2a6-291">因此，減少片段著色器中的作業數目，通常可以在端點著色器中提供比優化更佳的效能提升。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-291">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="fe2a6-292">Unity 標準著色器替代專案</span><span class="sxs-lookup"><span data-stu-id="fe2a6-292">Unity Standard shader alternatives</span></span>

<span data-ttu-id="fe2a6-293">您不需要使用以實體為基礎的轉譯（.PBR）或其他高品質的著色器，而是瞭解如何利用更高效能且更便宜的著色器。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-293">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="fe2a6-294">[Mixed Reality 工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組提供已針對混合現實專案優化的[MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-294">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="fe2a6-295">Unity 也提供 unlit、頂點亮、擴散和其他簡化的著色器選項，相較于 Unity 標準著色器，速度明顯更快。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-295">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="fe2a6-296">如需詳細資訊，請參閱[內建著色器的使用方式和效能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-296">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="fe2a6-297">著色器預先載入</span><span class="sxs-lookup"><span data-stu-id="fe2a6-297">Shader preloading</span></span>

<span data-ttu-id="fe2a6-298">使用*著色器預先載入*和其他訣竅來優化[著色器載入時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-298">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="fe2a6-299">特別是，著色器預先載入表示您不會因為執行時間著色器編譯而看到任何 hitches。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-299">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="fe2a6-300">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="fe2a6-300">Limit overdraw</span></span>

<span data-ttu-id="fe2a6-301">在 Unity 中，您可以切換**場景視圖**左上角的 [[**繪製模式] 功能表**](https://docs.unity3d.com/Manual/ViewModes.html)，然後選取 [**過度繪製**]，以顯示其場景的過度繪製。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-301">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="fe2a6-302">一般來說，在將物件傳送至 GPU 之前，您可以先將它們先行剔除，藉以減輕過度繪製。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-302">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="fe2a6-303">Unity 提供為其引擎執行[遮蔽剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-303">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="fe2a6-304">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="fe2a6-304">Memory recommendations</span></span>

<span data-ttu-id="fe2a6-305">記憶體配置過多 & 解除配置作業可能會對您的全像應用程式造成不良的影響，因而導致效能不一致、凍結的框架和其他不利的行為。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-305">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="fe2a6-306">在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-306">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="fe2a6-307">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="fe2a6-307">Garbage collection</span></span>

<span data-ttu-id="fe2a6-308">當 GC 啟動以分析不在執行期間的範圍中的物件，而且需要釋放其記憶體時，自動製作的應用程式將會遺失垃圾收集行程（GC）的計算時間，因此可供重複使用。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-308">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for re-use.</span></span> <span data-ttu-id="fe2a6-309">常數配置和取消配置通常需要更頻繁地執行垃圾收集行程，因而會影響效能和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-309">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="fe2a6-310">Unity 提供了絕佳的頁面，詳細說明垃圾收集行程的運作方式，以及在記憶體管理方面撰寫更有效率的程式碼的秘訣。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-310">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="fe2a6-311">優化 Unity 遊戲中的垃圾收集</span><span class="sxs-lookup"><span data-stu-id="fe2a6-311">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="fe2a6-312">導致過多垃圾收集的其中一個最常見做法是不會快取 Unity 開發中元件和類別的參考。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-312">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="fe2a6-313">任何參考都應該在開始（）或喚醒（）期間捕捉，然後在更新（）或 LateUpdate （）等功能中重複使用。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-313">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="fe2a6-314">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="fe2a6-314">Other quick tips:</span></span>
- <span data-ttu-id="fe2a6-315">使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#類別，在執行時間以動態方式建立複雜字串</span><span class="sxs-lookup"><span data-stu-id="fe2a6-315">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="fe2a6-316">當不再需要 Log （）的呼叫時，請將其移除，因為它們仍會在應用程式的所有組建版本中執行</span><span class="sxs-lookup"><span data-stu-id="fe2a6-316">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="fe2a6-317">如果您的全像攝影應用程式通常需要大量的記憶體，請考慮在載入階段期間（例如，在呈現載入或轉換畫面時[ _**）呼叫 system.object**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-317">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="fe2a6-318">物件共用</span><span class="sxs-lookup"><span data-stu-id="fe2a6-318">Object pooling</span></span>

<span data-ttu-id="fe2a6-319">物件共用是一種常用的技術，可降低連續配置 & 取消設定物件的成本。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-319">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="fe2a6-320">這是藉由配置相同物件的大型集區，並重複使用此集區中的非作用中、可用的實例來完成，而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-320">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="fe2a6-321">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-321">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="fe2a6-322">Unity 中的物件共用教學課程</span><span class="sxs-lookup"><span data-stu-id="fe2a6-322">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="fe2a6-323">啟動效能</span><span class="sxs-lookup"><span data-stu-id="fe2a6-323">Startup performance</span></span>

<span data-ttu-id="fe2a6-324">您應該考慮使用較小的場景來啟動您的應用程式，然後使用 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 來載入場景的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-324">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="fe2a6-325">這可讓您的應用程式盡可能快速地進入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-325">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="fe2a6-326">請注意，當新場景啟動時可能會有大型的 CPU 尖峰，而且任何轉譯的內容可能會斷斷續續或有所不便。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-326">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="fe2a6-327">解決這個情況的方法之一，就是在載入的場景上將 AsyncOperation allowSceneActivation 屬性設為 "false"，等待場景載入，將畫面清除為黑色，然後將它設回 "true" 以完成場景啟用。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-327">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen to black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="fe2a6-328">請記住，當啟動場景正在載入時，會向使用者顯示全像攝影畫面。</span><span class="sxs-lookup"><span data-stu-id="fe2a6-328">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe2a6-329">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe2a6-329">See also</span></span>
- [<span data-ttu-id="fe2a6-330">優化 Unity 遊戲中的圖形轉譯</span><span class="sxs-lookup"><span data-stu-id="fe2a6-330">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="fe2a6-331">優化 Unity 遊戲中的垃圾收集</span><span class="sxs-lookup"><span data-stu-id="fe2a6-331">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="fe2a6-332">[物理最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-332">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="fe2a6-333">[優化腳本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="fe2a6-333">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
