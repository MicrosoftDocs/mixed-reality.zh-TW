---
title: 場景理解 SDK
description: 場景理解 SDK 的程式設計指南
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解，空間對應，Windows Mixed Reality，Unity
ms.openlocfilehash: eb2c6d88ce5a5ba637976a7d67abfdc2763c1674
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345678"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="fa32e-104">場景理解 SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="fa32e-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="fa32e-105">場景理解的目標是要轉換混合現實裝置所捕捉到的非結構化環境感應器資料，並將它轉換成可直覺且易於開發的功能強大但抽象化的標記法。</span><span class="sxs-lookup"><span data-stu-id="fa32e-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="fa32e-106">SDK 會作為應用程式與場景理解執行時間之間的通訊層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="fa32e-107">其目的是要模擬現有的標準結構，例如3D 呈現的3D 場景圖形，以及2d 應用程式的2D 矩形和麵板。</span><span class="sxs-lookup"><span data-stu-id="fa32e-107">It's aimed to mimic existing standard constructs such as 3D scene graphs for 3D representations and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="fa32e-108">雖然結構的場景理解模擬會對應到您可能使用的具體架構，但在一般的 SceneUnderstanding 中，不會有架構中立，允許在與它互動的不同架構之間進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="fa32e-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="fa32e-109">隨著場景的理解發展，SDK 的角色是為了確保新的標記法和功能會繼續在統一的架構中公開。</span><span class="sxs-lookup"><span data-stu-id="fa32e-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="fa32e-110">在本檔中，我們會先引進高階概念，協助您熟悉開發環境/使用方式，然後針對特定的類別和結構提供更詳細的檔。</span><span class="sxs-lookup"><span data-stu-id="fa32e-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="fa32e-111">哪裡可以取得 SDK？</span><span class="sxs-lookup"><span data-stu-id="fa32e-111">Where do I get the SDK?</span></span>

<span data-ttu-id="fa32e-112">SceneUnderstanding SDK 可透過 NuGet 下載。</span><span class="sxs-lookup"><span data-stu-id="fa32e-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="fa32e-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="fa32e-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="fa32e-114">**注意：** 最新版本取決於預覽套件，而您必須啟用發行前版本套件才能看到它。</span><span class="sxs-lookup"><span data-stu-id="fa32e-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="fa32e-115">從版本 0.5.2022-rc，場景理解支援 c # 和 c + + 的語言投影，讓應用程式可以開發適用于 Win32 或 UWP 平臺的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fa32e-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="fa32e-116">在此版本中，SceneUnderstanding 支援使用 unity 的編輯器支援，而使 SceneObserver 僅用於與 HoloLens2 通訊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="fa32e-117">SceneUnderstanding 需要18362或更高版本 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="fa32e-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="fa32e-118">如果您在 Unity 專案中使用 SDK，請使用適用于[unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity)將套件安裝到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="fa32e-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="fa32e-119">概觀說明</span><span class="sxs-lookup"><span data-stu-id="fa32e-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="fa32e-120">場景</span><span class="sxs-lookup"><span data-stu-id="fa32e-120">The Scene</span></span>

<span data-ttu-id="fa32e-121">您的混合現實裝置會持續整合其在您環境中所見到的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="fa32e-122">場景瞭解漏斗圖所有這些資料來源，並產生一個單一的統一抽象概念。</span><span class="sxs-lookup"><span data-stu-id="fa32e-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="fa32e-123">場景理解會產生場景，這是代表單一事物（例如牆/天花板/樓層）實例的[SceneObjects](scene-understanding-SDK.md#sceneobjects)組合。場景物件本身是[SceneComponents](scene-understanding-SDK.md#scenecomponents)的組合，代表組成此 SceneObject 的更細微部分。</span><span class="sxs-lookup"><span data-stu-id="fa32e-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="fa32e-124">元件的範例包括四邊形和網格，但未來可能會代表周框方塊、碰撞網格、中繼資料等。</span><span class="sxs-lookup"><span data-stu-id="fa32e-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="fa32e-125">將原始感應器資料轉換成場景的程式，是可能耗費資源的作業，可能需要幾秒鐘的時間（約10x10m）到幾分鐘，才會有非常大的空間（~ 50x50m），因此不會在沒有應用程式要求的情況下，由裝置所計算的東西。</span><span class="sxs-lookup"><span data-stu-id="fa32e-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="fa32e-126">相反地，場景產生是由您的應用程式隨選觸發。</span><span class="sxs-lookup"><span data-stu-id="fa32e-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="fa32e-127">SceneObserver 類別具有可計算或還原序列化場景的靜態方法，您可以接著列舉/與之互動。</span><span class="sxs-lookup"><span data-stu-id="fa32e-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="fa32e-128">「計算」動作會隨選執行，並在 CPU 上執行，但在不同的進程（混合現實驅動程式）中執行。</span><span class="sxs-lookup"><span data-stu-id="fa32e-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="fa32e-129">不過，雖然我們會在另一個進程中計算，但產生的場景資料會儲存在應用程式的場景物件中並加以維護。</span><span class="sxs-lookup"><span data-stu-id="fa32e-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="fa32e-130">以下圖表說明此流程流程，並顯示兩個應用程式與場景理解執行時間互動的範例。</span><span class="sxs-lookup"><span data-stu-id="fa32e-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![處理圖表](images/SU-ProcessFlow.png)

<span data-ttu-id="fa32e-132">左側是混合現實執行時間的圖表，它一律開啟並在自己的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="fa32e-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="fa32e-133">此執行時間會負責執行裝置追蹤、空間對應，以及場景理解用來瞭解有關世界的原因的其他作業。</span><span class="sxs-lookup"><span data-stu-id="fa32e-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="fa32e-134">在圖表的右側，我們會顯示兩個理論上的應用程式，讓您使用場景理解。</span><span class="sxs-lookup"><span data-stu-id="fa32e-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="fa32e-135">第一個應用程式介面的 MRTK 會在內部使用場景理解 SDK，第二個應用程式會計算並使用兩個不同的場景實例。</span><span class="sxs-lookup"><span data-stu-id="fa32e-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="fa32e-136">此圖表中的所有3個場景都會產生不同的場景實例，而驅動程式不會追蹤全域狀態，而在某個場景中的應用程式和場景物件之間，則不會在另一個場景中找到。</span><span class="sxs-lookup"><span data-stu-id="fa32e-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="fa32e-137">場景理解提供一段時間的追蹤機制，但這是使用 SDK 來完成的，而執行這項追蹤的程式碼則是在應用程式的 SDK 中執行。</span><span class="sxs-lookup"><span data-stu-id="fa32e-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="fa32e-138">因為每個場景都會將它的資料儲存在您應用程式的記憶體空間中，所以您可以假設場景物件或其內部資料的所有函式一律會在應用程式的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="fa32e-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="fa32e-139">Layout</span><span class="sxs-lookup"><span data-stu-id="fa32e-139">Layout</span></span>

<span data-ttu-id="fa32e-140">若要使用場景理解，請務必瞭解並瞭解執行時間如何在邏輯上或實際地代表元件。</span><span class="sxs-lookup"><span data-stu-id="fa32e-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="fa32e-141">場景代表具有特定版面配置的資料，而該配置已選擇簡單，同時維持 pliable 以符合未來需求的基礎結構，而不需要主要的修訂。</span><span class="sxs-lookup"><span data-stu-id="fa32e-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="fa32e-142">此場景的運作方式是將所有元件（所有場景物件的建立區塊）儲存在一般清單中，並透過參考（其中特定元件會參考其他專案）來定義階層和組合。</span><span class="sxs-lookup"><span data-stu-id="fa32e-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="fa32e-143">在下方，我們以其平面和邏輯形式呈現結構的範例。</span><span class="sxs-lookup"><span data-stu-id="fa32e-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="fa32e-144">邏輯版面配置</span><span class="sxs-lookup"><span data-stu-id="fa32e-144">Logical Layout</span></span></th><th><span data-ttu-id="fa32e-145">實體配置</span><span class="sxs-lookup"><span data-stu-id="fa32e-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="fa32e-146">場景</span><span class="sxs-lookup"><span data-stu-id="fa32e-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="fa32e-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="fa32e-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="fa32e-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="fa32e-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="fa32e-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="fa32e-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="fa32e-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="fa32e-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="fa32e-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="fa32e-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="fa32e-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="fa32e-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="fa32e-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="fa32e-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="fa32e-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="fa32e-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="fa32e-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="fa32e-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="fa32e-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="fa32e-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="fa32e-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="fa32e-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="fa32e-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="fa32e-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="fa32e-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="fa32e-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="fa32e-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="fa32e-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="fa32e-164">下圖將重點放在場景的實體和邏輯版面配置之間的差異。</span><span class="sxs-lookup"><span data-stu-id="fa32e-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="fa32e-165">在左側，我們會看到您的應用程式在列舉場景時所看到之資料的階層式配置。</span><span class="sxs-lookup"><span data-stu-id="fa32e-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="fa32e-166">在右側，我們看到場景實際上是由12個相異元件所組成，視需要個別存取。</span><span class="sxs-lookup"><span data-stu-id="fa32e-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="fa32e-167">在處理新場景時，我們預期應用程式會以邏輯方式將此階層引導，不過，在場景更新之間進行追蹤時，某些應用程式可能只會對以兩個場景之間共用的特定元件為目標感興趣。</span><span class="sxs-lookup"><span data-stu-id="fa32e-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="fa32e-168">API 概觀</span><span class="sxs-lookup"><span data-stu-id="fa32e-168">API overview</span></span>

<span data-ttu-id="fa32e-169">下一節提供場景理解中之結構的高階總覽。</span><span class="sxs-lookup"><span data-stu-id="fa32e-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="fa32e-170">閱讀本節可讓您瞭解場景的呈現方式，以及各種元件的用途/用途。</span><span class="sxs-lookup"><span data-stu-id="fa32e-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="fa32e-171">下一節將提供在此總覽中說明 mda 的具體程式碼範例和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fa32e-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="fa32e-172">以下所述的所有類型都位於 `Microsoft.MixedReality.SceneUnderstanding` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="fa32e-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="fa32e-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="fa32e-173">SceneComponents</span></span>

<span data-ttu-id="fa32e-174">現在您已瞭解幕後的邏輯版面配置，現在可以呈現 SceneComponents 的概念，以及如何使用它們來撰寫階層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="fa32e-175">SceneComponents 是 SceneUnderstanding 中最細微的分解，代表單一核心的事物，例如網格或四個或周框方塊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="fa32e-176">SceneComponents 是可以獨立更新並可由其他 SceneComponents 參考的專案，因此，它們有一個唯一識別碼的單一全域屬性，可允許這種類型的追蹤/參考機制。</span><span class="sxs-lookup"><span data-stu-id="fa32e-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="fa32e-177">識別碼用於場景階層的邏輯組合以及物件持續性（更新一個場景相對於另一個場景的動作）。</span><span class="sxs-lookup"><span data-stu-id="fa32e-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="fa32e-178">如果您將每個新計算的場景都視為相異，而且只要列舉其中的所有資料，則識別碼對您而言都是透明的。</span><span class="sxs-lookup"><span data-stu-id="fa32e-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="fa32e-179">不過，如果您打算追蹤多個更新的元件，您會使用識別碼來編制索引，並尋找場景物件之間的 SceneComponents。</span><span class="sxs-lookup"><span data-stu-id="fa32e-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="fa32e-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="fa32e-180">SceneObjects</span></span>

<span data-ttu-id="fa32e-181">SceneObject 是一種 SceneComponent，代表「事物」的實例，例如牆、樓層、上限等等。以其 Kind 屬性工作表示。</span><span class="sxs-lookup"><span data-stu-id="fa32e-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="fa32e-182">SceneObjects 是幾何，因此具有在空間中代表其位置的函式和屬性，但不包含任何幾何或邏輯結構。</span><span class="sxs-lookup"><span data-stu-id="fa32e-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="fa32e-183">相反地，SceneObjects 參考其他 SceneComponents，特別是 SceneQuads 和 SceneMeshes，可提供系統支援的各種標記法。</span><span class="sxs-lookup"><span data-stu-id="fa32e-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="fa32e-184">計算新場景時，您的應用程式很可能會列舉場景的 SceneObjects 來處理其感興趣的內容。</span><span class="sxs-lookup"><span data-stu-id="fa32e-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="fa32e-185">SceneObjects 可以有下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="fa32e-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="fa32e-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="fa32e-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="fa32e-187">描述</span><span class="sxs-lookup"><span data-stu-id="fa32e-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="fa32e-188">背景</span><span class="sxs-lookup"><span data-stu-id="fa32e-188">Background</span></span></td><td><span data-ttu-id="fa32e-189">已知 SceneObject<b>不</b>是其他可辨識類型的場景物件之一。</span><span class="sxs-lookup"><span data-stu-id="fa32e-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="fa32e-190">此類別不應與 [不明] 混淆，其中的背景已知不是牆/樓層/上限等等 .。。雖然不明尚未分類。</span><span class="sxs-lookup"><span data-stu-id="fa32e-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="fa32e-191">內牆</span><span class="sxs-lookup"><span data-stu-id="fa32e-191">Wall</span></span></td><td><span data-ttu-id="fa32e-192">實體牆。</span><span class="sxs-lookup"><span data-stu-id="fa32e-192">A physical wall.</span></span> <span data-ttu-id="fa32e-193">牆會假設為 immovable 環境結構。</span><span class="sxs-lookup"><span data-stu-id="fa32e-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="fa32e-194">樓層</span><span class="sxs-lookup"><span data-stu-id="fa32e-194">Floor</span></span></td><td><span data-ttu-id="fa32e-195">樓層是其中一個可以進行的任何表面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="fa32e-196">注意：樓梯不是樓層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-196">Note: stairs are not floors.</span></span> <span data-ttu-id="fa32e-197">另請注意，該樓層會假設任何 walkable 介面，因此不會明確假設為單一樓層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="fa32e-198">多層結構、斜坡等等 .。。全都分類為樓層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="fa32e-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="fa32e-199">Ceiling</span></span></td><td><span data-ttu-id="fa32e-200">房間的上方表面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="fa32e-201">平台</span><span class="sxs-lookup"><span data-stu-id="fa32e-201">Platform</span></span></td><td><span data-ttu-id="fa32e-202">您可以放置全息影像的大型平面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="fa32e-203">這些通常會代表資料表、countertops 和其他大型水準表面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="fa32e-204">World</span><span class="sxs-lookup"><span data-stu-id="fa32e-204">World</span></span></td><td><span data-ttu-id="fa32e-205">標記不可知之幾何資料的保留標籤。</span><span class="sxs-lookup"><span data-stu-id="fa32e-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="fa32e-206">藉由設定 EnableWorldMesh 更新旗標所產生的網格會分類為「世界」。</span><span class="sxs-lookup"><span data-stu-id="fa32e-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="fa32e-207">Unknown</span><span class="sxs-lookup"><span data-stu-id="fa32e-207">Unknown</span></span></td><td><span data-ttu-id="fa32e-208">這個場景物件尚未分類並指派一種類型。</span><span class="sxs-lookup"><span data-stu-id="fa32e-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="fa32e-209">這不應該與背景混淆，因為此物件可能是任何專案，系統還不會為其提供強大的分類。</span><span class="sxs-lookup"><span data-stu-id="fa32e-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="fa32e-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="fa32e-210">SceneMesh</span></span>

<span data-ttu-id="fa32e-211">SceneMesh 是一種 SceneComponent，其使用三角形清單來接近任意幾何物件的幾何。</span><span class="sxs-lookup"><span data-stu-id="fa32e-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="fa32e-212">SceneMeshes 是用於數個不同的內容中，它們可以代表防水資料格結構的元件，或做為 WorldMesh，代表與場景相關聯的未系結空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="fa32e-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="fa32e-213">每個網格所提供的索引和頂點資料，都會使用與用來在所有新式轉譯 Api 中呈現三角形網格的[頂點和索引緩衝區](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx)相同的熟悉配置。</span><span class="sxs-lookup"><span data-stu-id="fa32e-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="fa32e-214">請注意，在場景理解中，網格會使用32位索引，而且可能需要細分為特定轉譯引擎的區塊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="fa32e-215">纏繞順序和座標系統</span><span class="sxs-lookup"><span data-stu-id="fa32e-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="fa32e-216">場景理解所產生的所有網格預期會使用順時針的纏繞順序，在右手座標系統中傳回網格。</span><span class="sxs-lookup"><span data-stu-id="fa32e-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="fa32e-217">注意：191105之前的作業系統組建可能有已知的錯誤，其中「世界」網格已以逆時針的纏繞順序傳回，而後續已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="fa32e-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="fa32e-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="fa32e-218">SceneQuad</span></span>

<span data-ttu-id="fa32e-219">SceneQuad 是代表佔據3d 世界之2d 表面的 SceneComponent。</span><span class="sxs-lookup"><span data-stu-id="fa32e-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="fa32e-220">SceneQuads 的使用方式類似于 ARKit ARPlaneAnchor 或 ARCore 平面，但它們提供更高階的功能，做為一般應用程式或增強 UX 所使用的2d 畫布。</span><span class="sxs-lookup"><span data-stu-id="fa32e-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="fa32e-221">2D 特定 Api 是針對讓放置和版面配置便於使用的四邊形所提供，而使用四邊形的開發（除了轉譯外）應該比使用3d 網格更類似于2d 畫布。</span><span class="sxs-lookup"><span data-stu-id="fa32e-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="fa32e-222">SceneQuad 圖形</span><span class="sxs-lookup"><span data-stu-id="fa32e-222">SceneQuad shape</span></span>

<span data-ttu-id="fa32e-223">SceneQuads 定義2d 中的界限矩形介面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="fa32e-224">不過，SceneQuads 是以任意且可能複雜的圖形（例如環圈形的形狀表）來代表表面。若要表示四個表面的複雜圖形，您可以使用 GetSurfaceMask API，將介面的形狀轉譯至您所提供的影像緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fa32e-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="fa32e-225">如果具有四個的 SceneObject 也有網格，則網格三角形應該等同于此轉譯影像，而兩者都代表表面的真正幾何，只是2d 或3d 座標。</span><span class="sxs-lookup"><span data-stu-id="fa32e-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="fa32e-226">場景瞭解 SDK 詳細資料和參考</span><span class="sxs-lookup"><span data-stu-id="fa32e-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="fa32e-227">下一節將協助您熟悉 SceneUnderstanding 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="fa32e-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="fa32e-228">這一節應該會提供您基本知識，此時您應該有足夠的內容可以流覽範例應用程式，以查看如何全面性地使用 SceneUnderstanding。</span><span class="sxs-lookup"><span data-stu-id="fa32e-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="fa32e-229">初始化</span><span class="sxs-lookup"><span data-stu-id="fa32e-229">Initialization</span></span>

<span data-ttu-id="fa32e-230">使用 SceneUnderstanding 的第一個步驟是讓您的應用程式取得場景物件的參考。</span><span class="sxs-lookup"><span data-stu-id="fa32e-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="fa32e-231">這可以透過兩種方式的其中一種來完成，也可以由驅動程式來計算場景，或在過去計算的現有場景可以取消序列化。</span><span class="sxs-lookup"><span data-stu-id="fa32e-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="fa32e-232">後者特別適用于在開發期間使用 SceneUnderstanding，其中應用程式和體驗可以在沒有混合現實裝置的情況下快速建立原型。</span><span class="sxs-lookup"><span data-stu-id="fa32e-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="fa32e-233">場景會使用 SceneObserver 來計算。</span><span class="sxs-lookup"><span data-stu-id="fa32e-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="fa32e-234">在建立場景之前，您的應用程式應該查詢您的裝置，以確保它支援 SceneUnderstanding，以及要求使用者存取 SceneUnderstanding 所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="fa32e-235">如果未呼叫 RequestAccessAsync （），則計算新場景將會失敗。</span><span class="sxs-lookup"><span data-stu-id="fa32e-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="fa32e-236">接下來，我們將計算一個以混合現實耳機為基礎的新場景，並具有10個計量半徑。</span><span class="sxs-lookup"><span data-stu-id="fa32e-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="fa32e-237">從資料初始化（也稱為</span><span class="sxs-lookup"><span data-stu-id="fa32e-237">Initialization from Data (aka.</span></span> <span data-ttu-id="fa32e-238">電腦路徑）</span><span class="sxs-lookup"><span data-stu-id="fa32e-238">the PC Path)</span></span>

<span data-ttu-id="fa32e-239">雖然可以針對直接耗用量來計算場景，但也可以使用序列化形式來計算，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="fa32e-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="fa32e-240">這已證明在開發時非常有用，因為它可讓開發人員在不需要裝置的情況下工作並測試場景理解。</span><span class="sxs-lookup"><span data-stu-id="fa32e-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="fa32e-241">將場景序列化的動作和計算方式幾乎相同，資料會傳回到您的應用程式，而不是由 SDK 在本機進行還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa32e-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="fa32e-242">接著，您可以自行將其還原序列化，或儲存以供日後使用。</span><span class="sxs-lookup"><span data-stu-id="fa32e-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="fa32e-243">SceneObject 列舉</span><span class="sxs-lookup"><span data-stu-id="fa32e-243">SceneObject Enumeration</span></span>

<span data-ttu-id="fa32e-244">既然您的應用程式有一個場景，您的應用程式就會查看 SceneObjects 並與之互動。</span><span class="sxs-lookup"><span data-stu-id="fa32e-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="fa32e-245">這是藉由存取**SceneObjects**屬性來完成：</span><span class="sxs-lookup"><span data-stu-id="fa32e-245">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="fa32e-246">元件更新和重新尋找元件</span><span class="sxs-lookup"><span data-stu-id="fa32e-246">Component update and re-finding components</span></span>

<span data-ttu-id="fa32e-247">還有另一個函式可抓取場景中稱為***sys.application.findcomponent***的元件。</span><span class="sxs-lookup"><span data-stu-id="fa32e-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="fa32e-248">當更新追蹤物件，並在後續的幕後尋找時，此函式會很有用。</span><span class="sxs-lookup"><span data-stu-id="fa32e-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="fa32e-249">下列程式碼會計算相對於前一個場景的新場景，然後在新場景中尋找樓層。</span><span class="sxs-lookup"><span data-stu-id="fa32e-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="fa32e-250">從場景物件存取網格和四邊形</span><span class="sxs-lookup"><span data-stu-id="fa32e-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="fa32e-251">一旦找到 SceneObjects，您的應用程式很可能會想要存取包含在其所組成之四邊形/網格中的資料。</span><span class="sxs-lookup"><span data-stu-id="fa32e-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="fa32e-252">此資料會使用***四邊形***和***網格***屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="fa32e-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="fa32e-253">下列程式碼將列舉 floor 物件的所有四邊形和網格。</span><span class="sxs-lookup"><span data-stu-id="fa32e-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="fa32e-254">請注意，它是具有相對於場景原點之轉換的 SceneObject。</span><span class="sxs-lookup"><span data-stu-id="fa32e-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="fa32e-255">這是因為 SceneObject 代表「事物」的實例，並且會在空間中定位，四邊形和網格代表相對於其父系的轉換幾何。</span><span class="sxs-lookup"><span data-stu-id="fa32e-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="fa32e-256">不同的 SceneObjects 可以參考相同的 SceneMesh/SceneQuad SceneComponents，也可能是 SceneObject 有一個以上的 SceneMesh/SceneQuad。</span><span class="sxs-lookup"><span data-stu-id="fa32e-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="fa32e-257">處理轉換</span><span class="sxs-lookup"><span data-stu-id="fa32e-257">Dealing with Transforms</span></span>

<span data-ttu-id="fa32e-258">在處理轉換時，場景理解已刻意嘗試配合傳統的3D 場景標記法。</span><span class="sxs-lookup"><span data-stu-id="fa32e-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="fa32e-259">因此，每個場景會限制為單一座標系統，與最常見的3D 環境表示相同。</span><span class="sxs-lookup"><span data-stu-id="fa32e-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="fa32e-260">SceneObjects 每個都會提供其位置作為座標系統內的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="fa32e-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="fa32e-261">如果您的應用程式正在處理的場景會延伸單一來源提供的限制，可將 SceneObjects 錨定至 SpatialAnchors，或產生數個場景並將它們合併在一起，但為了簡單起見，我們假設防水場景存在於其本身的原始來源中，而這些專案是由場景所定義的一個同位來當地語系化。 OriginSpatialGraphNodeId。</span><span class="sxs-lookup"><span data-stu-id="fa32e-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="fa32e-262">例如，下列 Unity 程式碼示範如何使用 Windows 認知和 Unity Api，將座標系統對齊在一起。</span><span class="sxs-lookup"><span data-stu-id="fa32e-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="fa32e-263">如需有關如何取得對應于 Unity 世界來源的 SpatialCoordinateSystem，以及在和之間進行轉換的擴充方法，請參閱[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)和[SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，以取得有關 Windows 認知 api 的詳細資料，以及[Unity 中的混合現實原生物件](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) `.ToUnity()` `System.Numerics.Matrix4x4` `UnityEngine.Matrix4x4` 。</span><span class="sxs-lookup"><span data-stu-id="fa32e-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="fa32e-264">每個 `SceneObject` 都有一個 `Position` 和 `Orientation` 屬性，可用來定位相對於包含之來源的對應內容 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="fa32e-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="fa32e-265">例如，下列範例假設遊戲是場景根目錄的子系，並指派其本機位置和旋轉以配合指定的 `SceneObject` ：</span><span class="sxs-lookup"><span data-stu-id="fa32e-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="fa32e-266">&</span><span class="sxs-lookup"><span data-stu-id="fa32e-266">Quad</span></span>

<span data-ttu-id="fa32e-267">四邊形的設計目的是為了加速2D 放置案例，而且應該將其視為2D 畫布 UX 元素的擴充。</span><span class="sxs-lookup"><span data-stu-id="fa32e-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="fa32e-268">雖然四邊形是 SceneObjects 的元件，而且可以在3D 中轉譯，但四個 Api 本身會假設四邊形是2D 結構。</span><span class="sxs-lookup"><span data-stu-id="fa32e-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="fa32e-269">它們提供一些資訊，例如範圍、圖形，以及提供放置的 Api。</span><span class="sxs-lookup"><span data-stu-id="fa32e-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="fa32e-270">四邊形有矩形範圍，但它們代表任意形狀的2D 介面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="fa32e-271">若要在這些2D 介面上啟用放置，這些介面會與3D 環境四邊形供應專案公用程式互動，以實現這種互動。</span><span class="sxs-lookup"><span data-stu-id="fa32e-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="fa32e-272">目前場景理解提供兩個這類函數： **FindCentermostPlacement**和**GetOcclusionMask**。</span><span class="sxs-lookup"><span data-stu-id="fa32e-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="fa32e-273">FindCentermostPlacement 是高階 API，它會找出可放置物件的四個位置，並嘗試尋找您的物件的最佳位置，以確保您提供的周框方塊會位於基礎介面上。</span><span class="sxs-lookup"><span data-stu-id="fa32e-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="fa32e-274">下列範例顯示如何尋找 centermost 可放置位置，並將全息圖形錨定到四個。</span><span class="sxs-lookup"><span data-stu-id="fa32e-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="fa32e-275">步驟1-4 高度相依于您的特定架構/執行，但主題應該類似。</span><span class="sxs-lookup"><span data-stu-id="fa32e-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="fa32e-276">請務必注意，四個部分只代表在空間中當地語系化的界限2D 平面。</span><span class="sxs-lookup"><span data-stu-id="fa32e-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="fa32e-277">藉由讓您的引擎/架構知道四個的位置，並將您的物件與四個相對應，您的全息影像將會正確地放在真實世界。</span><span class="sxs-lookup"><span data-stu-id="fa32e-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="fa32e-278">如需詳細資訊，請參閱四邊形上的範例，其中會顯示特定的實作為。</span><span class="sxs-lookup"><span data-stu-id="fa32e-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="fa32e-279">網狀</span><span class="sxs-lookup"><span data-stu-id="fa32e-279">Mesh</span></span>

<span data-ttu-id="fa32e-280">網格代表物件或環境的幾何標記法。</span><span class="sxs-lookup"><span data-stu-id="fa32e-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="fa32e-281">與[空間對應](spatial-mapping.md)一樣，每個空間 surface 網格提供的網格索引和頂點資料，都會使用與在所有新式轉譯 api 中用來呈現三角形網格的頂點和索引緩衝區相同的熟悉配置。</span><span class="sxs-lookup"><span data-stu-id="fa32e-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="fa32e-282">頂點位置會在的座標系統中提供 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="fa32e-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="fa32e-283">用來參考此資料的特定 Api 如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa32e-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="fa32e-284">下列程式碼提供從網格結構產生三角形清單的範例：</span><span class="sxs-lookup"><span data-stu-id="fa32e-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="fa32e-285">索引/頂點緩衝區必須 >= 索引/頂點計數，否則可以任意調整大小，以便有效率地重複使用記憶體。</span><span class="sxs-lookup"><span data-stu-id="fa32e-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="fa32e-286">使用場景稍微瞭解進行開發</span><span class="sxs-lookup"><span data-stu-id="fa32e-286">Developing with scene understandings</span></span>

<span data-ttu-id="fa32e-287">此時，您應該瞭解場景瞭解執行時間和 SDK 的核心建立區塊。</span><span class="sxs-lookup"><span data-stu-id="fa32e-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="fa32e-288">大部分的威力和複雜度都是在存取模式中、與3D 架構的互動，以及可以在這些 Api 之上撰寫的工具，以執行更先進的工作，例如空間規劃、房間分析、流覽、物理等。我們希望能夠以適當的方式來捕捉這些範例，以讓您的案例更有説明。</span><span class="sxs-lookup"><span data-stu-id="fa32e-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="fa32e-289">如果有範例/案例未解決，請讓我們知道，我們會嘗試記錄/原型您需要的內容。</span><span class="sxs-lookup"><span data-stu-id="fa32e-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="fa32e-290">哪裡可以取得範例程式碼？</span><span class="sxs-lookup"><span data-stu-id="fa32e-290">Where can I get sample code?</span></span>

<span data-ttu-id="fa32e-291">您可以在我們的[Unity 範例頁面](https://github.com/sceneunderstanding-microsoft/unitysample)頁面上找到適用于 unity 的場景範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa32e-291">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="fa32e-292">此應用程式可讓您與您的裝置通訊並轉譯各種場景物件，或者，它可讓您在電腦上載入序列化的場景，並讓您在不使用裝置的情況下體驗到場景的瞭解。</span><span class="sxs-lookup"><span data-stu-id="fa32e-292">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="fa32e-293">哪裡可以取得範例場景？</span><span class="sxs-lookup"><span data-stu-id="fa32e-293">Where can I get sample scenes?</span></span>

<span data-ttu-id="fa32e-294">如果您有 HoloLens2，可以將 ComputeSerializedAsync 的輸出儲存至檔案，並以您自己的便利性將它還原序列化，以儲存您所捕捉到的任何場景。</span><span class="sxs-lookup"><span data-stu-id="fa32e-294">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="fa32e-295">如果您沒有 HoloLens2 裝置，但想要使用場景理解來播放，您必須下載預先捕捉的場景。</span><span class="sxs-lookup"><span data-stu-id="fa32e-295">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="fa32e-296">場景理解範例目前隨附于序列化的幕後，可供您自行下載並使用。</span><span class="sxs-lookup"><span data-stu-id="fa32e-296">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="fa32e-297">您可以在這裡找到：</span><span class="sxs-lookup"><span data-stu-id="fa32e-297">You can find them here:</span></span>

[<span data-ttu-id="fa32e-298">場景瞭解範例場景</span><span class="sxs-lookup"><span data-stu-id="fa32e-298">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="fa32e-299">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa32e-299">See also</span></span>

* [<span data-ttu-id="fa32e-300">空間對應</span><span class="sxs-lookup"><span data-stu-id="fa32e-300">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="fa32e-301">場景理解</span><span class="sxs-lookup"><span data-stu-id="fa32e-301">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="fa32e-302">Unity 範例</span><span class="sxs-lookup"><span data-stu-id="fa32e-302">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
