---
title: 對 Unity 的效能建議
description: 使用混合實境應用程式改善效能的 Unity 特有秘訣。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形, cpu, gpu, 轉譯, 記憶體回收行程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 18691ab7993b2802268d3c4ce05532dfa5bd1723
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160014"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="51a80-104">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="51a80-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="51a80-105">本文是以[混合實境效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unity 引擎環境的特定學習。</span><span class="sxs-lookup"><span data-stu-id="51a80-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="51a80-106">使用建議的 Unity 專案設定</span><span class="sxs-lookup"><span data-stu-id="51a80-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="51a80-107">將 Unity 中的混合實境應用程式效能最佳化時，最重要的第一個步驟是確定您已使用 [Unity 的建議環境設定](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="51a80-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you are using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="51a80-108">該文章包含的內容具有一些最重要的場景設定，適用於建立高效能的混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="51a80-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="51a80-109">其中一些建議的設定也會反白顯示，如下所示。</span><span class="sxs-lookup"><span data-stu-id="51a80-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="51a80-110">如何使用 Unity 進行分析</span><span class="sxs-lookup"><span data-stu-id="51a80-110">How to profile with Unity</span></span>

<span data-ttu-id="51a80-111">Unity 提供內建的 **[Unity 分析工具](https://docs.unity3d.com/Manual/Profiler.html)** ，這是一項絕佳資源，可讓您針對特定應用程式收集寶貴的效能深入解析。</span><span class="sxs-lookup"><span data-stu-id="51a80-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="51a80-112">雖然使用者可以在編輯器中執行分析工具，但這些計量並不代表真正的執行時間環境，因此應謹慎使用這些結果。</span><span class="sxs-lookup"><span data-stu-id="51a80-112">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="51a80-113">當您在裝置上執行應用程式時，建議從遠端分析應用程式，以取得最精確且可採取動作的深入解析。</span><span class="sxs-lookup"><span data-stu-id="51a80-113">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="51a80-114">此外，也可使用 Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)，這個工具非常強大且深入解析。</span><span class="sxs-lookup"><span data-stu-id="51a80-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="51a80-115">Unity 提供的絕佳文件：</span><span class="sxs-lookup"><span data-stu-id="51a80-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="51a80-116">如何從遠端將 [Unity 分析工具連線到 UWP 應用程式](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="51a80-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="51a80-117">如何使用 Unity 分析工具有效率地[診斷效能問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="51a80-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="51a80-118">當 Unity 分析工具已連線並新增 GPU 分析工具之後 (請參閱右上角的「新增分析工具」  )，使用者可以在分析工具的中間查看 CPU 與 GPU 分別花費了多少時間。</span><span class="sxs-lookup"><span data-stu-id="51a80-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="51a80-119">這可讓開發人員在其應用程式為 CPU 或 GPU 限定時，取得快速近似值。</span><span class="sxs-lookup"><span data-stu-id="51a80-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="51a80-121">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="51a80-121">CPU performance recommendations</span></span>

<span data-ttu-id="51a80-122">以下內容涵蓋更深入的效能實務，特別將目標放在 Unity 與 C# 開發。</span><span class="sxs-lookup"><span data-stu-id="51a80-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="51a80-123">快取參考</span><span class="sxs-lookup"><span data-stu-id="51a80-123">Cache references</span></span>

<span data-ttu-id="51a80-124">最佳做法是在初始化時快取所有相關元件和 GameObject 的參考。</span><span class="sxs-lookup"><span data-stu-id="51a80-124">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="51a80-125">這是因為相對於儲存指標的記憶體成本，重複的函式呼叫 (例如 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* ) 會大幅提高成本。</span><span class="sxs-lookup"><span data-stu-id="51a80-125">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="51a80-126">這也適用於經常使用的 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。</span><span class="sxs-lookup"><span data-stu-id="51a80-126">This also applies to to the very regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="51a80-127">*Camera.main* 只會使用底下的 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，以高成本的方式搜尋場景圖形中含有 *"MainCamera"* 標記的相機物件。</span><span class="sxs-lookup"><span data-stu-id="51a80-127">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="51a80-128">避免 GetComponent(字串)</span><span class="sxs-lookup"><span data-stu-id="51a80-128">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="51a80-129">使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 時，有少數不同的多載。</span><span class="sxs-lookup"><span data-stu-id="51a80-129">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="51a80-130">請務必一律使用以類型為基礎的實作，而不是使用以字串為基礎的搜尋多載。</span><span class="sxs-lookup"><span data-stu-id="51a80-130">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="51a80-131">在場景中依字串搜尋會比依類型搜尋昂貴許多。</span><span class="sxs-lookup"><span data-stu-id="51a80-131">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="51a80-132">(良好) Component GetComponent(輸入類型)</span><span class="sxs-lookup"><span data-stu-id="51a80-132">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="51a80-133">(良好) T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="51a80-133">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="51a80-134">(不良) Component GetComponent(字串)></span><span class="sxs-lookup"><span data-stu-id="51a80-134">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="51a80-135">避免高成本的作業</span><span class="sxs-lookup"><span data-stu-id="51a80-135">Avoid expensive operations</span></span>

1) <span data-ttu-id="51a80-136">**避免使用 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="51a80-136">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="51a80-137">雖然 LINQ 可能會非常簡潔且易於讀寫，但相較於手動撰寫演算法，通常需要更多的計算以及更多的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="51a80-137">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="51a80-138">**通用 Unity API**</span><span class="sxs-lookup"><span data-stu-id="51a80-138">**Common Unity APIs**</span></span>

    <span data-ttu-id="51a80-139">某些 Unity API 雖然很有用，但執行的成本可能很高。</span><span class="sxs-lookup"><span data-stu-id="51a80-139">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="51a80-140">其中大部分牽涉到在整個場景圖形中搜尋一些相符的 Gameobject 清單。</span><span class="sxs-lookup"><span data-stu-id="51a80-140">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="51a80-141">這些作業通常可加以避免，方法是快取參考或針對有問題的 GameObject 實作管理員元件，以便在執行時間追蹤參考。</span><span class="sxs-lookup"><span data-stu-id="51a80-141">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="51a80-142">應不計代價消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 。</span><span class="sxs-lookup"><span data-stu-id="51a80-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="51a80-143">這些函式可能會比直接函式呼叫慢大約 1000 倍。</span><span class="sxs-lookup"><span data-stu-id="51a80-143">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="51a80-144">**注意 Box 處理**</span><span class="sxs-lookup"><span data-stu-id="51a80-144">**Beware of boxing**</span></span>

    <span data-ttu-id="51a80-145">[Box 處理](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 語言和執行時間的核心概念。</span><span class="sxs-lookup"><span data-stu-id="51a80-145">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="51a80-146">這是將實值類型變數 (例如 char、int、bool 等) 包裝成參考類型變數的程序。</span><span class="sxs-lookup"><span data-stu-id="51a80-146">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="51a80-147">當實值類型變數為 "boxed" 時，會包裝在儲存於受管理堆積上的 System.Object 中。</span><span class="sxs-lookup"><span data-stu-id="51a80-147">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="51a80-148">因此，系統會配置記憶體，且最終在處置時必須由記憶體回收行程處理。</span><span class="sxs-lookup"><span data-stu-id="51a80-148">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="51a80-149">這些配置和取消配置會產生效能成本，且在許多情況下並不需要，或是可以輕鬆地以較不昂貴的替代方案來取代。</span><span class="sxs-lookup"><span data-stu-id="51a80-149">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="51a80-150">開發中最常見的 Box 處理形式之一，是使用[可為 Null 的實值類型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。</span><span class="sxs-lookup"><span data-stu-id="51a80-150">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="51a80-151">通常會想要能夠針對函式中的實值類型傳回 null，特別是當作業嘗試取得值時，可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="51a80-151">It is common to want to be able to return null for a value type in a function, especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="51a80-152">這種方法的潛在問題，是現在會在堆積上進行配置，因此需要在稍後進行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="51a80-152">The potential problem with this approach is that allocation now occurs on the heap and consequently needs to be garbage collected later.</span></span>

    <span data-ttu-id="51a80-153">**C# 中的 Box 處理範例**</span><span class="sxs-lookup"><span data-stu-id="51a80-153">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="51a80-154">**透過可為 Null 的實值類型進行有問題 Box 處理的範例**</span><span class="sxs-lookup"><span data-stu-id="51a80-154">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="51a80-155">此程式碼會示範一個可在 Unity 專案中建立的虛擬粒子類別。</span><span class="sxs-lookup"><span data-stu-id="51a80-155">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="51a80-156">呼叫 `TryGetSpeed()` 將會導致堆積上的物件配置，而這將需要在稍後的時間點進行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="51a80-156">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="51a80-157">這個範例特別有問題，因為場景中可能有超過 1000 個以上的粒子，而每個粒子都被要求其目前的速度。</span><span class="sxs-lookup"><span data-stu-id="51a80-157">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="51a80-158">因此，1000 多個物件會受到配置，因而每個畫面格都會解除配置，這會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="51a80-158">Thus, 1000's of objects would be allocated and consequently de-allocated every frame, which would greatly diminish performance.</span></span> <span data-ttu-id="51a80-159">重新撰寫函式以傳回負數值 (例如 -1) 來表示失敗則可避免這個問題，並將記憶體保留在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="51a80-159">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="51a80-160">重複的程式碼路徑</span><span class="sxs-lookup"><span data-stu-id="51a80-160">Repeating code paths</span></span>

<span data-ttu-id="51a80-161">任何重複的 Unity 回呼函式 (亦即</span><span class="sxs-lookup"><span data-stu-id="51a80-161">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="51a80-162">Update)，每秒和/或每個畫面格會執行許多次，都應該非常小心地撰寫。</span><span class="sxs-lookup"><span data-stu-id="51a80-162">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="51a80-163">在此，任何高成本的作業都會對效能產生巨大且一致的影響。</span><span class="sxs-lookup"><span data-stu-id="51a80-163">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="51a80-164">**空白的回呼函式**</span><span class="sxs-lookup"><span data-stu-id="51a80-164">**Empty callback functions**</span></span>

    <span data-ttu-id="51a80-165">雖然在您的應用程式中保留下列程式碼可能看似無害，特別是因為每個 Unity 指令碼都會使用此程式碼區塊自動初始化，但這些空白回呼實際上可能會非常昂貴。</span><span class="sxs-lookup"><span data-stu-id="51a80-165">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="51a80-166">Unity 會在未受管理/受管理程式碼界限 (在 UnityEngine 程式碼與您的應用程式程式碼) 之間來回操作。</span><span class="sxs-lookup"><span data-stu-id="51a80-166">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="51a80-167">即使沒有要執行的內容，透過此橋接器切換內容的成本也相當高。</span><span class="sxs-lookup"><span data-stu-id="51a80-167">Context switching over this bridge is fairly expensive, even if there is nothing to execute.</span></span> <span data-ttu-id="51a80-168">如果您應用程式的 100 多個 GameObject 具有包含空白重複 Unity 回呼的元件，這會變得特別有問題。</span><span class="sxs-lookup"><span data-stu-id="51a80-168">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="51a80-169">Update() 是這個效能問題最常見的表現，但其他重複的 Unity 回呼 (例如下列情況) 可能會同樣不良 (若非更差狀況)：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等等。</span><span class="sxs-lookup"><span data-stu-id="51a80-169">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="51a80-170">**偏好每個畫面格執行一次的作業**</span><span class="sxs-lookup"><span data-stu-id="51a80-170">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="51a80-171">下列 Unity API 是許多全像攝影應用程式的常見作業。</span><span class="sxs-lookup"><span data-stu-id="51a80-171">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="51a80-172">雖然不一定能夠這麼做，但這些函式的結果通常可計算一次，且結果會在指定畫面格的整個應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="51a80-172">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="51a80-173">a) 一般而言，最好具有專用的單一類別或服務來處理場景中的注視 Raycast，然後在所有其他場景元件中重複使用這個結果，而不是每個元件都進行重複且基本上都相同的 Raycast 作業。</span><span class="sxs-lookup"><span data-stu-id="51a80-173">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="51a80-174">當然，有些應用程式可能需要不同來源，或是針對不同 [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html) 的 Raycast。</span><span class="sxs-lookup"><span data-stu-id="51a80-174">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="51a80-175">b) 避免重複 Unity 回呼 (例如 Update()) 中的 GetComponent() 作業，方法是在 Start() 或 Awake() 中[快取參考](#cache-references)</span><span class="sxs-lookup"><span data-stu-id="51a80-175">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="51a80-176">c) 最佳做法是在初始化時將所有物件具現化 (若可能)，並使用[物件集區](#object-pooling)，以在應用程式的整個執行時間回收並重複使用 GameObject</span><span class="sxs-lookup"><span data-stu-id="51a80-176">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="51a80-177">**避免介面和虛擬結構**</span><span class="sxs-lookup"><span data-stu-id="51a80-177">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="51a80-178">透過介面與直接物件來叫用函式呼叫或呼叫虛擬函式，通常比使用直接結構或直接函式呼叫的成本更高。</span><span class="sxs-lookup"><span data-stu-id="51a80-178">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="51a80-179">如果虛擬函式或介面不是必要的，則應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="51a80-179">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="51a80-180">不過，如果利用這些方法可簡化開發共同作業、程式碼可讀性和程式碼維護性，那麼這些方法的效能衝擊通常值得取捨。</span><span class="sxs-lookup"><span data-stu-id="51a80-180">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="51a80-181">一般來說，建議不要將欄位和函式標示為虛擬，除非有清楚的預期需要覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="51a80-181">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="51a80-182">對於在每個畫面格上呼叫多次的高頻率程式碼路徑，或甚至是每個畫面格呼叫一次 (例如 `UpdateUI()` 方法)，都應該特別小心。</span><span class="sxs-lookup"><span data-stu-id="51a80-182">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="51a80-183">**避免以傳值方式傳遞結構**</span><span class="sxs-lookup"><span data-stu-id="51a80-183">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="51a80-184">不同於類別，結構是實值類型，而當直接傳遞至函式時，會將其內容複製到新建立的實例。</span><span class="sxs-lookup"><span data-stu-id="51a80-184">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="51a80-185">此複本會增加 CPU 成本，以及堆疊上的額外記憶體。</span><span class="sxs-lookup"><span data-stu-id="51a80-185">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="51a80-186">針對小型結構，效果通常非常小，因此可接受。</span><span class="sxs-lookup"><span data-stu-id="51a80-186">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="51a80-187">不過，對於每個畫面格重複叫用的函式，以及接受大型結構的函式，如果可能，請將函式定義修改為以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="51a80-187">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="51a80-188">請於此處深入了解</span><span class="sxs-lookup"><span data-stu-id="51a80-188">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="51a80-189">其他</span><span class="sxs-lookup"><span data-stu-id="51a80-189">Miscellaneous</span></span>

1) <span data-ttu-id="51a80-190">**物理特性**</span><span class="sxs-lookup"><span data-stu-id="51a80-190">**Physics**</span></span>

    <span data-ttu-id="51a80-191">a) 一般而言，改善物理特性最簡單的方式，是限制花費在「物理特性」上的時間量，或每秒的反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="51a80-191">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="51a80-192">當然，這會降低模擬準確度。</span><span class="sxs-lookup"><span data-stu-id="51a80-192">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="51a80-193">請參閱 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="51a80-193">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="51a80-194">b) Unity 中的碰撞器類型具有廣泛不同的效能特性。</span><span class="sxs-lookup"><span data-stu-id="51a80-194">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="51a80-195">下列順序從左至右列出最高效能的碰撞器到最低效能的碰撞器。</span><span class="sxs-lookup"><span data-stu-id="51a80-195">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="51a80-196">請務必避免網格碰撞器，這比基本碰撞器的成本高出許多。</span><span class="sxs-lookup"><span data-stu-id="51a80-196">It is most important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="51a80-197">如需詳細資訊，請參閱 [Unity 物理特性最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="51a80-197">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="51a80-198">**動畫**</span><span class="sxs-lookup"><span data-stu-id="51a80-198">**Animations**</span></span>

    <span data-ttu-id="51a80-199">停用閒置動畫，方法是停用 Animator 元件 (停用遊戲物件不會有相同的效果)。</span><span class="sxs-lookup"><span data-stu-id="51a80-199">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="51a80-200">避免設計出 Animator 所在迴圈將值設定為相同內容的模式。</span><span class="sxs-lookup"><span data-stu-id="51a80-200">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="51a80-201">這項技術會有相當大的負擔，對應用程式則沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="51a80-201">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="51a80-202">請於此處深入了解。</span><span class="sxs-lookup"><span data-stu-id="51a80-202">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="51a80-203">**複雜演算法**</span><span class="sxs-lookup"><span data-stu-id="51a80-203">**Complex algorithms**</span></span>

    <span data-ttu-id="51a80-204">如果您的應用程式是使用複雜演算法，例如反向運動、路徑尋找等等，請試著尋找較簡單的方法，或調整其效能的相關設定</span><span class="sxs-lookup"><span data-stu-id="51a80-204">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="51a80-205">CPU 對 GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="51a80-205">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="51a80-206">一般來說，CPU 對 GPU 的效能會降至提交到圖形卡的**繪製呼叫**。</span><span class="sxs-lookup"><span data-stu-id="51a80-206">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="51a80-207">為改善效能，必須策略性地將繪製呼叫**降低**或**重建**，以獲得最佳結果。</span><span class="sxs-lookup"><span data-stu-id="51a80-207">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="51a80-208">由於繪製呼叫本身會耗用大量資源，因此減少繪製呼叫會降低所需的整體工作量。</span><span class="sxs-lookup"><span data-stu-id="51a80-208">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="51a80-209">此外，在繪製呼叫之間的狀態變更需要在圖形驅動程式中進行高成本驗證和轉譯步驟，因此，重建應用程式的繪製呼叫來限制狀態變更 (亦即</span><span class="sxs-lookup"><span data-stu-id="51a80-209">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="51a80-210">不同的資料等) 可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="51a80-210">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="51a80-211">Unity 有一篇很棒的文章，可讓您大致瞭解並探討其平台的批次繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="51a80-211">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="51a80-212">Unity 繪製呼叫批次處理</span><span class="sxs-lookup"><span data-stu-id="51a80-212">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="51a80-213">單通道執行個體化轉譯</span><span class="sxs-lookup"><span data-stu-id="51a80-213">Single pass instanced rendering</span></span>

<span data-ttu-id="51a80-214">Unity 中的 [單通道執行個體化轉譯] 可讓您將每個眼球的繪製呼叫降低至一個執行個體化的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="51a80-214">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="51a80-215">由於兩個繪製呼叫之間的快取一致性，GPU 上也有一些效能改善。</span><span class="sxs-lookup"><span data-stu-id="51a80-215">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="51a80-216">若要在 Unity 專案中啟用這項功能</span><span class="sxs-lookup"><span data-stu-id="51a80-216">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="51a80-217">開啟 [Player XR 設定]  (移至 [編輯]   > [專案設定]   > [播放器]   > [XR 設定]  )</span><span class="sxs-lookup"><span data-stu-id="51a80-217">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="51a80-218">從 [立體聲轉譯方法]  下拉式功能表中，選取 [單通道執行個體化]  (必須核取 [支援的虛擬實境]  核取方塊)</span><span class="sxs-lookup"><span data-stu-id="51a80-218">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="51a80-219">如需此轉譯方法的詳細資料，請在 Unity 中參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="51a80-219">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="51a80-220">如何使用進階的立體聲轉譯將 AR 和 VR 效能最大化</span><span class="sxs-lookup"><span data-stu-id="51a80-220">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="51a80-221">單通道執行個體</span><span class="sxs-lookup"><span data-stu-id="51a80-221">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="51a80-222">如果開發人員已經有非針對執行個體撰寫的現有自訂著色器，就會發生單通道執行個體化轉譯的一個常見問題。</span><span class="sxs-lookup"><span data-stu-id="51a80-222">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="51a80-223">啟用這項功能之後，開發人員可能會注意到，有些 GameObject 只會在單一眼球中轉譯。</span><span class="sxs-lookup"><span data-stu-id="51a80-223">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="51a80-224">這是因為相關聯的自訂著色器沒有適當的執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="51a80-224">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="51a80-225">如需解決此問題的方法，請參閱 Unity 中的[適用於 HoloLens 的單通道立體聲轉譯](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)</span><span class="sxs-lookup"><span data-stu-id="51a80-225">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="51a80-226">靜態批次處理</span><span class="sxs-lookup"><span data-stu-id="51a80-226">Static batching</span></span>

<span data-ttu-id="51a80-227">Unity 能夠批次處理許多靜態物件，以減少對 GPU 的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="51a80-227">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="51a80-228">靜態批次處理適用於 Unity 中大部分的[轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)物件，這些物件會 **1) 共用相同的資料** 且 \*\*2) 全部標示為 [靜態] \*\* (在 Unity 中選取物件，然後按一下偵測器右上方的核取方塊)。</span><span class="sxs-lookup"><span data-stu-id="51a80-228">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="51a80-229">標記為「靜態」  的 GameObject 無法在整個應用程式的執行時間移動。</span><span class="sxs-lookup"><span data-stu-id="51a80-229">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="51a80-230">因此，靜態批次處理可能很容易在 HoloLens 上運用，因為幾乎每個物件都必須放置、移動、調整等等。針對沉浸式頭戴裝置，靜態批次處理可以大幅減少繪製呼叫，因而改善效能。</span><span class="sxs-lookup"><span data-stu-id="51a80-230">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="51a80-231">如需詳細資料，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「靜態批次處理」  。</span><span class="sxs-lookup"><span data-stu-id="51a80-231">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="51a80-232">動態批次處理</span><span class="sxs-lookup"><span data-stu-id="51a80-232">Dynamic batching</span></span>

<span data-ttu-id="51a80-233">由於將 HoloLens 開發的物件標示為「靜態」  會有問題，因此動態批次處理可能是彌補這項缺乏功能的絕佳工具。</span><span class="sxs-lookup"><span data-stu-id="51a80-233">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="51a80-234">當然，該功能也適用於沉浸式頭戴裝置。</span><span class="sxs-lookup"><span data-stu-id="51a80-234">Of course, it can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="51a80-235">不過，Unity 中的動態批次處理可能難以啟用，因為 GameObject 必須 **a) 共用相同的資料** 且 **b) 符合一長串的其他條件**。</span><span class="sxs-lookup"><span data-stu-id="51a80-235">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="51a80-236">如需完整清單，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「動態批次處理」  。</span><span class="sxs-lookup"><span data-stu-id="51a80-236">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="51a80-237">最常見的情況是，因為相關聯的網格資料不能超過 300 個頂點，所以 GameObject 會變成無效而無法動態地進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="51a80-237">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="51a80-238">其他技術</span><span class="sxs-lookup"><span data-stu-id="51a80-238">Other techniques</span></span>

<span data-ttu-id="51a80-239">只有在多個 GameObject 可以共用相同的資料時，才會進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="51a80-239">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="51a80-240">一般而言，這會因為需要 GameObject 而受到封鎖，使其各自的材質獲得獨特的紋理。</span><span class="sxs-lookup"><span data-stu-id="51a80-240">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="51a80-241">通常會將「紋理」結合成一個大「紋理」，這是一種稱為[紋理圖集](https://en.wikipedia.org/wiki/Texture_atlas)的方法。</span><span class="sxs-lookup"><span data-stu-id="51a80-241">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="51a80-242">此外，通常最好是在可能且合理的情況下，將網格結合成一個 GameObject。</span><span class="sxs-lookup"><span data-stu-id="51a80-242">Furthermore, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="51a80-243">Unity 中的每個轉譯器都會有其相關聯的繪製呼叫，而不會在單一轉譯器下提交合併的網格。</span><span class="sxs-lookup"><span data-stu-id="51a80-243">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="51a80-244">在執行時間修改 Renderer.material 的屬性，會建立一份資料複本，因此可能會中斷批次處理。</span><span class="sxs-lookup"><span data-stu-id="51a80-244">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="51a80-245">使用 Renderer.sharedMaterial 來修改 Gameobject 之間的共用材質屬性。</span><span class="sxs-lookup"><span data-stu-id="51a80-245">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="51a80-246">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="51a80-246">GPU performance recommendations</span></span>

<span data-ttu-id="51a80-247">深入瞭解如何[將 Unity 中的圖形轉譯進行最佳化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="51a80-247">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="51a80-248">將深度緩衝區共用進行最佳化</span><span class="sxs-lookup"><span data-stu-id="51a80-248">Optimize depth buffer sharing</span></span>

<span data-ttu-id="51a80-249">通常建議您啟用 [Player XR 設定]  下的 [深度緩衝區共用]  ，以將[全像投影穩定性](Hologram-stability.md)進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="51a80-249">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="51a80-250">不過，使用此設定來啟用深度延遲階段重新投影時，建議選取 [16 位元深度格式]  ，而不是 [24 位元深度格式]  。</span><span class="sxs-lookup"><span data-stu-id="51a80-250">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="51a80-251">16 位元深度緩衝區會大幅降低與深度緩衝區流量相關聯的頻寬 (和電源)。</span><span class="sxs-lookup"><span data-stu-id="51a80-251">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="51a80-252">這在降低電源和改善效能方面都是一大優勢。</span><span class="sxs-lookup"><span data-stu-id="51a80-252">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="51a80-253">不過，使用「16 位元深度格式」  可能會有兩個負面結果。</span><span class="sxs-lookup"><span data-stu-id="51a80-253">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="51a80-254">**Z 衝突**</span><span class="sxs-lookup"><span data-stu-id="51a80-254">**Z-Fighting**</span></span>

<span data-ttu-id="51a80-255">降低的深度範圍精確度會使 [z 衝突](https://en.wikipedia.org/wiki/Z-fighting)較可能發生在 16 位元而非 24 位元。</span><span class="sxs-lookup"><span data-stu-id="51a80-255">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="51a80-256">若要避免這些成品，請修改 [Unity 攝影機](https://docs.unity3d.com/Manual/class-Camera.html)的近/遠裁剪平面，以降低精確度。</span><span class="sxs-lookup"><span data-stu-id="51a80-256">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="51a80-257">對於 HoloLens 型應用程式，50m 的遠裁剪平面而非 Unity 預設的 1000m 裁剪平面通常可以排除任何 z 衝突。</span><span class="sxs-lookup"><span data-stu-id="51a80-257">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="51a80-258">**已停用的樣板緩衝區**</span><span class="sxs-lookup"><span data-stu-id="51a80-258">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="51a80-259">當 Unity 建立[具有 16 位元深度的轉譯紋理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)時，並不會建立樣板緩衝區。</span><span class="sxs-lookup"><span data-stu-id="51a80-259">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="51a80-260">根據 Unity 文件選取 24 位元深度格式，將會建立 24 位元的 z 緩衝區，以及 [8 位元樣板緩衝區] (https://docs.unity3d.com/Manual/SL-Stencil.html) (如果裝置適用 32 位元，這通常是 HoloLens 之類的情況)。</span><span class="sxs-lookup"><span data-stu-id="51a80-260">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="51a80-261">避免全螢幕效果</span><span class="sxs-lookup"><span data-stu-id="51a80-261">Avoid full-screen effects</span></span>

<span data-ttu-id="51a80-262">在全螢幕上操作的技術可能會相當高成本，因為其大小順序是每個畫面格數百萬個作業。</span><span class="sxs-lookup"><span data-stu-id="51a80-262">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="51a80-263">因此，建議您避免[後置處理效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html) (例如消除鋸齒、綻開等等)。</span><span class="sxs-lookup"><span data-stu-id="51a80-263">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="51a80-264">最佳光源設定</span><span class="sxs-lookup"><span data-stu-id="51a80-264">Optimal lighting settings</span></span>

<span data-ttu-id="51a80-265">Unity 中的[即時全域照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供優異的視覺結果，但牽涉到相當高成本的光源計算。</span><span class="sxs-lookup"><span data-stu-id="51a80-265">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="51a80-266">建議您透過 [視窗]   > [轉譯]   > [光源設定]  > 取消核取 [即時全域照明]  ，停用每個 Unity 場景檔案的即時全域照明。</span><span class="sxs-lookup"><span data-stu-id="51a80-266">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="51a80-267">此外，建議停用所有陰影轉換，因為這些也會在 Unity 場景上增加高成本的 GPU 通道。</span><span class="sxs-lookup"><span data-stu-id="51a80-267">Furthermore, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="51a80-268">可針對光源停用陰影，也可以透過 [品質] 設定進行全面性控制。</span><span class="sxs-lookup"><span data-stu-id="51a80-268">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="51a80-269">[編輯]   > [專案設定]  ，然後選取 [品質]  類別 > 針對 UWP 平台，選取 [低品質]  。</span><span class="sxs-lookup"><span data-stu-id="51a80-269">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="51a80-270">使用者也可以只將 [陰影]  屬性設定為 [停用陰影]  。</span><span class="sxs-lookup"><span data-stu-id="51a80-270">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="51a80-271">減少多邊形計數</span><span class="sxs-lookup"><span data-stu-id="51a80-271">Reduce poly count</span></span>

<span data-ttu-id="51a80-272">多邊形計數通常會縮減為</span><span class="sxs-lookup"><span data-stu-id="51a80-272">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="51a80-273">從場景移除物件</span><span class="sxs-lookup"><span data-stu-id="51a80-273">Removing objects from a scene</span></span>
2) <span data-ttu-id="51a80-274">資產減去，可減少指定網格的多邊形數目</span><span class="sxs-lookup"><span data-stu-id="51a80-274">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="51a80-275">將[詳細資料的層級 (LOD) 系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)實作到您的應用程式中，以相同幾何的較低多邊形版本呈現遙遠的物件</span><span class="sxs-lookup"><span data-stu-id="51a80-275">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="51a80-276">瞭解 Unity 中的著色器</span><span class="sxs-lookup"><span data-stu-id="51a80-276">Understanding shaders in Unity</span></span>

<span data-ttu-id="51a80-277">比較效能中著色器的簡單近似值，是識別在執行時間每個執行的平均作業數目。</span><span class="sxs-lookup"><span data-stu-id="51a80-277">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="51a80-278">這可以在 Unity 中輕鬆完成。</span><span class="sxs-lookup"><span data-stu-id="51a80-278">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="51a80-279">選取您的著色器資產或選取材質，然後在偵測器視窗的右上角，選取後接 [選取著色器]  的齒輪圖示</span><span class="sxs-lookup"><span data-stu-id="51a80-279">Select your shader asset or select a material, then in the top right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![選取 Unity 中的著色器](images/Select-shader-unity.png)
2) <span data-ttu-id="51a80-281">選取著色器資產後，按一下偵測器視窗下的 [編譯並顯示程式碼]  按鈕</span><span class="sxs-lookup"><span data-stu-id="51a80-281">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中編譯著色器程式碼](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="51a80-283">編譯之後，在結果中尋找統計資料區段，其中包含頂點和像素著色器的不同作業數目 (注意：像素著色器通常也稱為片段著色器)</span><span class="sxs-lookup"><span data-stu-id="51a80-283">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 標準著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="51a80-285">最佳化像素著色器</span><span class="sxs-lookup"><span data-stu-id="51a80-285">Optimize pixel shaders</span></span>

<span data-ttu-id="51a80-286">使用上述方法查看編譯的統計資料結果，[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會比 [頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均執行更多作業。</span><span class="sxs-lookup"><span data-stu-id="51a80-286">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="51a80-287">片段著色器 (也稱為像素著色器) 會針對螢幕輸出上的每個像素執行，而頂點著色器只會針對繪製到螢幕的所有網格中每個頂點來執行。</span><span class="sxs-lookup"><span data-stu-id="51a80-287">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="51a80-288">因此，片段著色器不只會因所有光源計算而比頂點著色器有更多的指示，片段著色器通常還會在較大的資料集上執行。</span><span class="sxs-lookup"><span data-stu-id="51a80-288">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="51a80-289">例如，如果螢幕輸出是 2k 比 2k 影像，則片段著色器可執行 2,000\*2,000 = 4,000,000 次。</span><span class="sxs-lookup"><span data-stu-id="51a80-289">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="51a80-290">如果呈現兩眼，這個數字會加倍，因為有兩個畫面。</span><span class="sxs-lookup"><span data-stu-id="51a80-290">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="51a80-291">如果混合實境應用程式有多個通道、全螢幕後置處理效果，或將多個網格轉譯為相同的像素，這個數字就會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="51a80-291">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="51a80-292">因此，減少片段著色器中的作業數目，通常可以在端點著色器中提供比最佳化更佳的效能提升。</span><span class="sxs-lookup"><span data-stu-id="51a80-292">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="51a80-293">Unity 標準著色器作業</span><span class="sxs-lookup"><span data-stu-id="51a80-293">Unity Standard shader alternatives</span></span>

<span data-ttu-id="51a80-294">您不需要使用以實體為基礎的轉譯 (PBR) 或其他高品質的著色器，而是瞭解如何利用更高的效能及更低成本的著色器。</span><span class="sxs-lookup"><span data-stu-id="51a80-294">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="51a80-295">[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供已針對混合實境專案進行最佳化的 [MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。</span><span class="sxs-lookup"><span data-stu-id="51a80-295">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="51a80-296">Unity 也提供無光、頂點光、擴散和其他簡化的著色器選項，相較於 Unity 標準著色器，速度大幅提升。</span><span class="sxs-lookup"><span data-stu-id="51a80-296">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="51a80-297">如需詳細資訊，請參閱[內建著色器的用法和效能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="51a80-297">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="51a80-298">著色器預先載入</span><span class="sxs-lookup"><span data-stu-id="51a80-298">Shader preloading</span></span>

<span data-ttu-id="51a80-299">使用「著色器預先載入」  和其他訣竅，將[著色器載入時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="51a80-299">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="51a80-300">特別是，著色器預先載入表示您不會因為執行時間著色器編譯而看到任何停頓。</span><span class="sxs-lookup"><span data-stu-id="51a80-300">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="51a80-301">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="51a80-301">Limit overdraw</span></span>

<span data-ttu-id="51a80-302">在 Unity 中，使用者可以顯示其場景的過度繪製，方法是切換 [場景視圖]  左上角的 [[繪製模式] 功能表  ](https://docs.unity3d.com/Manual/ViewModes.html)，然後選取 [過度繪製]  。</span><span class="sxs-lookup"><span data-stu-id="51a80-302">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="51a80-303">一般來說，在將物件傳送至 GPU 之前，您可以將這些物件先行剔除，藉以減輕過度繪製。</span><span class="sxs-lookup"><span data-stu-id="51a80-303">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="51a80-304">Unity 提供針對其引擎實作[遮蔽剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="51a80-304">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="51a80-305">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="51a80-305">Memory recommendations</span></span>

<span data-ttu-id="51a80-306">記憶體過度配置及解除配置的作業可能會對您的全像攝影應用程式造成不良的影響，因而導致效能不一致、凍結的畫面格和其他不利的行為。</span><span class="sxs-lookup"><span data-stu-id="51a80-306">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="51a80-307">在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由記憶體回收行程所控制。</span><span class="sxs-lookup"><span data-stu-id="51a80-307">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="51a80-308">記憶體回收行程</span><span class="sxs-lookup"><span data-stu-id="51a80-308">Garbage collection</span></span>

<span data-ttu-id="51a80-309">當記憶體回收行程 (GC) 啟動以分析不在執行期間範圍中的物件，且需要釋放其記憶體時，全像攝影應用程式將會遺失處理記憶體回收行程的計算時間，因此可供重複使用。</span><span class="sxs-lookup"><span data-stu-id="51a80-309">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for re-use.</span></span> <span data-ttu-id="51a80-310">常數配置和取消配置通常需要更頻繁地執行記憶體回收行程，因而會影響效能和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="51a80-310">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="51a80-311">Unity 提供了絕佳的頁面，詳細說明記憶體回收行程的運作方式，以及在記憶體管理方面撰寫更有效率程式碼的秘訣。</span><span class="sxs-lookup"><span data-stu-id="51a80-311">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="51a80-312">將 Unity 遊戲中的記憶體回收行程進行最佳化</span><span class="sxs-lookup"><span data-stu-id="51a80-312">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="51a80-313">導致過多記憶體回收行程最常見的做法之一，是不會快取 Unity 開發中元件和類別的參考。</span><span class="sxs-lookup"><span data-stu-id="51a80-313">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="51a80-314">任何參考都應該在 Start() 或 Awake() 期間加以擷取，然後在 Update() 或 LateUpdate() 等函式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="51a80-314">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="51a80-315">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="51a80-315">Other quick tips:</span></span>
- <span data-ttu-id="51a80-316">使用 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 類別，在執行時間以動態方式建置複雜字串</span><span class="sxs-lookup"><span data-stu-id="51a80-316">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="51a80-317">當您不再需要 Debug.Log() 的呼叫時，請加以移除，因為該函式仍會在應用程式的所有組建版本中執行</span><span class="sxs-lookup"><span data-stu-id="51a80-317">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="51a80-318">如果您的全像攝影應用程式通常需要大量的記憶體，請考慮在載入階段 (例如，呈現載入或轉換畫面時) 呼叫 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)</span><span class="sxs-lookup"><span data-stu-id="51a80-318">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="51a80-319">物件集區</span><span class="sxs-lookup"><span data-stu-id="51a80-319">Object pooling</span></span>

<span data-ttu-id="51a80-320">物件集區是一種常用的技術，可降低連續配置及取消配置物件的成本。</span><span class="sxs-lookup"><span data-stu-id="51a80-320">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="51a80-321">這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="51a80-321">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="51a80-322">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="51a80-322">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="51a80-323">Unity 中的物件集區教學課程</span><span class="sxs-lookup"><span data-stu-id="51a80-323">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="51a80-324">啟動效能</span><span class="sxs-lookup"><span data-stu-id="51a80-324">Startup performance</span></span>

<span data-ttu-id="51a80-325">您應該考慮使用較小的場景來啟動您的應用程式，然後使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 載入場景的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="51a80-325">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="51a80-326">這可讓您的應用程式盡可能快速地進入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="51a80-326">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="51a80-327">請注意，當新的場景啟動時，可能會有大型的 CPU 尖峰，而且任何轉譯的內容可能會斷斷續續或是停頓。</span><span class="sxs-lookup"><span data-stu-id="51a80-327">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="51a80-328">解決這個情況的方法之一，就是在要載入的場景上，將 AsyncOperation.allowSceneActivation 屬性設為 "false"，等待場景載入，將畫面清除為黑色，然後將其設回 "true"，以完成場景啟用。</span><span class="sxs-lookup"><span data-stu-id="51a80-328">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen to black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="51a80-329">請記住，當啟動場景在載入時，會向使用者顯示全像攝影畫面。</span><span class="sxs-lookup"><span data-stu-id="51a80-329">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="51a80-330">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51a80-330">See also</span></span>
- [<span data-ttu-id="51a80-331">將 Unity 遊戲中的圖形轉譯進行最佳化</span><span class="sxs-lookup"><span data-stu-id="51a80-331">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="51a80-332">將 Unity 遊戲中的記憶體回收行程進行最佳化</span><span class="sxs-lookup"><span data-stu-id="51a80-332">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="51a80-333">[物理特性最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="51a80-333">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="51a80-334">[將指令碼進行最佳化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="51a80-334">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
