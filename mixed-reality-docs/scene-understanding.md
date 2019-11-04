---
title: 場景理解
description: 適用于 HoloLens 的場景理解功能簡介
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解，空間對應，Windows Mixed Reality，Unity
ms.openlocfilehash: 7ee0cf3af8012a053733896a8bf92192306b7f8b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437478"
---
# <a name="scene-understanding"></a><span data-ttu-id="79bd6-104">場景理解</span><span class="sxs-lookup"><span data-stu-id="79bd6-104">Scene understanding</span></span>

<span data-ttu-id="79bd6-105">場景理解為混合現實開發人員提供結構化的高階環境標記法，其設計目的是為了讓環保感知應用程式的開發更加直覺。</span><span class="sxs-lookup"><span data-stu-id="79bd6-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="79bd6-106">場景理解的運作方式是結合現有混合現實執行時間的強大功能，例如，高度精確的結構[空間對應](spatial-mapping.md)和新的 AI 驅動執行時間。</span><span class="sxs-lookup"><span data-stu-id="79bd6-106">Scene understanding does this by combining the power of existing mixed reality runtimes such as the highly accurate less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="79bd6-107">藉由結合這些技術，場景理解會產生類似于您在 Unity 或 ARKit/ARCore 等架構中使用之3D 環境的標記法。</span><span class="sxs-lookup"><span data-stu-id="79bd6-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="79bd6-108">場景理解進入點會以您應用程式所呼叫的場景觀察器作為開頭，以計算新場景。</span><span class="sxs-lookup"><span data-stu-id="79bd6-108">The Scene understanding entry point begins with a Scene Observer which is called by your application to compute a new scene.</span></span> <span data-ttu-id="79bd6-109">現今的技術能夠產生3個相異但相關的物件類別：簡化的防水環境網格，可推斷平面室結構，而不會雜亂、放置我們呼叫四邊形的平面區域，以及[空間對應](spatial-mapping.md)網格，與我們所呈現的四邊形/防水資料對齊。</span><span class="sxs-lookup"><span data-stu-id="79bd6-109">Today the technology is capable of generating 3 distinct but related object categories: simplified watertight environment meshes that infer the planar room structure without clutter, plane regions for placement that we call Quads, and a snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface.</span></span>

![空間對應網格，標示平面表面，防水網格](images/SUScenarios.png)

<span data-ttu-id="79bd6-111">本檔的目的是要提供案例總覽，並澄清場景瞭解和空間對應共用的關聯性。</span><span class="sxs-lookup"><span data-stu-id="79bd6-111">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span> <span data-ttu-id="79bd6-112">如需場景理解如何運作以及如何為其進行開發的詳細資訊，請參閱[場景瞭解 SDK 總覽](scene-understanding-SDK.md)檔。</span><span class="sxs-lookup"><span data-stu-id="79bd6-112">For details on how Scene understanding works and how to develop for it, please see the [Scene understanding SDK overview](scene-understanding-SDK.md) documentation.</span></span>

## <a name="device-support"></a><span data-ttu-id="79bd6-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="79bd6-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="79bd6-114"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="79bd6-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="79bd6-115"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="79bd6-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="79bd6-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="79bd6-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="79bd6-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="79bd6-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="79bd6-118">場景理解</span><span class="sxs-lookup"><span data-stu-id="79bd6-118">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="79bd6-119">✔️</span><span class="sxs-lookup"><span data-stu-id="79bd6-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="79bd6-120">常見使用案例</span><span class="sxs-lookup"><span data-stu-id="79bd6-120">Common usage scenarios</span></span>

<span data-ttu-id="79bd6-121">![常見的空間對應使用案例圖例：位置、遮蔽、物理和流覽](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="79bd6-121">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="79bd6-122">*常見的空間對應使用案例：位置、遮蔽、物理和導覽。*</span><span class="sxs-lookup"><span data-stu-id="79bd6-122">*Common spatial mapping usage scenarios: placement, occlusion, physics and navigation.*</span></span>

<br>

<span data-ttu-id="79bd6-123">環境感知應用程式的許多核心案例（放置、遮蔽、物理等等）都可透過空間對應和場景理解來定址，本節將強調這些差異。</span><span class="sxs-lookup"><span data-stu-id="79bd6-123">Many of the core scenarios for environment aware applications (placement, occlusion, physics, etc.) are addressable by both Spatial mapping and Scene understanding, this section highlights these differences.</span></span> <span data-ttu-id="79bd6-124">「場景理解」和「空間對應」之間的主要差異，是針對結構和簡易性的最大精確度和延遲進行取捨。</span><span class="sxs-lookup"><span data-stu-id="79bd6-124">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="79bd6-125">如果您的應用程式需要可能的最低延遲，而且只需要網格三角形，您會想要直接存取空間對應，不過，如果您要執行較高層級的處理，您可以考慮將它轉換成場景理解模型應該提供您功能的超集合。</span><span class="sxs-lookup"><span data-stu-id="79bd6-125">If your application requires the lowest-latency possible and requires mesh triangles only you will want to access Spatial Mapping directly, however if you are performing higher level processing you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="79bd6-126">另請注意，由於場景理解會提供空間對應網格做為其表示的一部分，因此您一律可以存取最完整且正確的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="79bd6-126">Also note, that because Scene understanding provides the spatial mapping mesh as part of its representation, you will always have access to the most complete and accurate spatial mapping data possible.</span></span>

 <span data-ttu-id="79bd6-127">下列各節會重新流覽新場景理解 SDK 內容中的核心空間對應案例。</span><span class="sxs-lookup"><span data-stu-id="79bd6-127">The following sections re-visit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="79bd6-128">位置</span><span class="sxs-lookup"><span data-stu-id="79bd6-128">Placement</span></span>

<span data-ttu-id="79bd6-129">場景理解提供專為簡化放置案例而設計的新結構。</span><span class="sxs-lookup"><span data-stu-id="79bd6-129">Scene understanding provides new constructs specifically designed to simplify placement scenarios.</span></span> <span data-ttu-id="79bd6-130">場景可以計算名為 SceneQuads 的基本型別，其中描述可以放置全息影像的平面表面。</span><span class="sxs-lookup"><span data-stu-id="79bd6-130">A scene can compute primitives called SceneQuads which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="79bd6-131">SceneQuads 特別設計于放置和描述2D 介面，並提供 API 以放置在介面上。</span><span class="sxs-lookup"><span data-stu-id="79bd6-131">SceneQuads have specifically been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="79bd6-132">先前，使用三角形網格來執行放置時，必須掃描所有的四個區域，並執行洞填滿/後置處理，以識別出適合物件放置的位置。</span><span class="sxs-lookup"><span data-stu-id="79bd6-132">Previously, when using the triangle mesh to perform placement, one had to scan all areas of the quad and perform hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="79bd6-133">這不一定是四邊形的必要，因為場景理解執行時間能夠推斷出四個未掃描的區域，而使四個不屬於介面的區域失效。</span><span class="sxs-lookup"><span data-stu-id="79bd6-133">This is not always necessary with Quads, as the Scene understanding runtime is capable of inferring which areas of the quad that were not scanned, and invalidate areas of the quad that are not part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="79bd6-134">已停用推斷的 ![SceneQuads，可捕捉掃描區域的放置區域。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="79bd6-134">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="79bd6-135">**影像 #1** -已停用推斷的 SceneQuads，可捕捉掃描區域的放置區域。</span><span class="sxs-lookup"><span data-stu-id="79bd6-135">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="79bd6-136">![四邊形，並已啟用推斷，則位置不再限於掃描的區域。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="79bd6-136">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="79bd6-137">**影像 #2** -已啟用推斷的四邊形，放置不再限於掃描的區域。</span><span class="sxs-lookup"><span data-stu-id="79bd6-137">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="79bd6-138">如果您的應用程式想要在您環境的固定結構上放置2D 或3D 全息，最好是從[空間對應](spatial-mapping.md)網格中計算這項資訊，以便於放置 SceneQuads 的簡單性和便利性。</span><span class="sxs-lookup"><span data-stu-id="79bd6-138">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="79bd6-139">如需本主題的詳細資訊，請參閱[場景瞭解 SDK 參考](scene-understanding-SDK.md)</span><span class="sxs-lookup"><span data-stu-id="79bd6-139">For more details on this topic, please see the [Scene understanding SDK reference](scene-understanding-SDK.md)</span></span>

<span data-ttu-id="79bd6-140">**注意**對於相依于空間對應網格的舊版放置程式碼，可以藉由設定 EnableWorldMesh 設定來計算空間對應網格和 SceneQuads。</span><span class="sxs-lookup"><span data-stu-id="79bd6-140">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="79bd6-141">如果場景理解 API 無法滿足您應用程式的延遲需求，我們建議您繼續使用[空間對應 API](spatial-mapping.md#placement)。</span><span class="sxs-lookup"><span data-stu-id="79bd6-141">If Scene understanding API does not satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="79bd6-142">遮蔽</span><span class="sxs-lookup"><span data-stu-id="79bd6-142">Occlusion</span></span>

<span data-ttu-id="79bd6-143">[空間對應遮蔽](spatial-mapping.md#occlusion)仍然是捕捉環境即時狀態的最不潛在方式。</span><span class="sxs-lookup"><span data-stu-id="79bd6-143">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="79bd6-144">雖然這可能有助於在高度動態的場景中提供遮蔽，但您可能會想要考慮針對遮蔽的場景理解，原因有好幾個。</span><span class="sxs-lookup"><span data-stu-id="79bd6-144">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="79bd6-145">如果您使用場景理解所產生的空間對應網格，您可以向空間對應要求不會儲存在本機快取中的資料，因此不會從認知 Api 提供給您。</span><span class="sxs-lookup"><span data-stu-id="79bd6-145">If you use the spatial mapping mesh generated by Scene Understanding you can request data from spatial mapping that would not be stored in the local cache and therefore not available to you from the perception APIs.</span></span> <span data-ttu-id="79bd6-146">使用遮蔽與防水網格的空間對應將會提供額外的價值，特別是完成未掃描的聊天室結構。</span><span class="sxs-lookup"><span data-stu-id="79bd6-146">Using Spatial Mapping for occlusion alongside watertight meshes will provide additional value, specifically completion of un-scanned room structure.</span></span>

<span data-ttu-id="79bd6-147">如果您的需求可容忍場景理解的延遲增加，應用程式開發人員應該考慮使用場景理解防水網格，而空間對應網格則與平面表示一致。</span><span class="sxs-lookup"><span data-stu-id="79bd6-147">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and presumably the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="79bd6-148">這會提供「兩個領域的最佳」，其中簡化的防水遮蔽會使用更精細的 nonplanar 幾何來提供最逼真的遮蔽地圖。</span><span class="sxs-lookup"><span data-stu-id="79bd6-148">This would provide a "best of both worlds" where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="79bd6-149">物理</span><span class="sxs-lookup"><span data-stu-id="79bd6-149">Physics</span></span>

<span data-ttu-id="79bd6-150">場景理解會產生防水網格，以明確地分解空間與語義，以解決空間對應網格所強加的許多物理限制。</span><span class="sxs-lookup"><span data-stu-id="79bd6-150">Scene understanding generates watertight meshes that decompose space with semantics specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="79bd6-151">防水結構可確保物理光線轉換一律會被叫用，而語義分解則允許針對室內導覽較簡單的 nav 網格產生。</span><span class="sxs-lookup"><span data-stu-id="79bd6-151">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="79bd6-152">如[遮蔽](#occlusion)使用 EnableSceneObjectMeshes 和 EnableWorldMesh 建立場景一節中所述，將會產生最能實際完成的網格。</span><span class="sxs-lookup"><span data-stu-id="79bd6-152">As described in the section on [occlusion](#occlusion) creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="79bd6-153">環境網格的 [防水] 屬性會防止點擊的測試無法到達介面，而網格資料會確保物理與場景中的所有物件互動，而不只是與房間結構互動。</span><span class="sxs-lookup"><span data-stu-id="79bd6-153">The watertight property of the environment mesh will prevent hit tests from failing to hit surfaces and the mesh data will ensure that physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="79bd6-154">瀏覽</span><span class="sxs-lookup"><span data-stu-id="79bd6-154">Navigation</span></span>

<span data-ttu-id="79bd6-155">依語義類別分解的平面網格是理想的導覽和路徑規劃結構，可簡化[空間對應導覽](spatial-mapping.md#navigation)總覽中所述的許多問題。</span><span class="sxs-lookup"><span data-stu-id="79bd6-155">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="79bd6-156">在場景中計算的 SceneMesh 物件已由表面類型取消群組，確保 nav 層代僅限於可以導覽的表面。</span><span class="sxs-lookup"><span data-stu-id="79bd6-156">The SceneMesh objects computed in the scene are already de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="79bd6-157">由於 floor 結構的簡單性，3d 引擎（例如 Unity）中的動態 nav 網格產生會根據即時需求而達到。</span><span class="sxs-lookup"><span data-stu-id="79bd6-157">Due to the simplicity of the floor structure, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="79bd6-158">產生精確的導覽網格目前仍需要後置處理，也就是應用程式仍然必須在樓層上進行阻隔器，以確保導覽不會通過雜亂/資料表等等 .。。完成此動作最精確的方式是，在使用 EnableWorldMesh 旗標來計算場景時，針對所提供的世界網格資料進行投影。</span><span class="sxs-lookup"><span data-stu-id="79bd6-158">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation does not pass through clutter/tables etc... The most accurate way to accomplish this is to project the world mesh data which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="79bd6-159">化</span><span class="sxs-lookup"><span data-stu-id="79bd6-159">Visualization</span></span>

<span data-ttu-id="79bd6-160">雖然[空間對應視覺效果](spatial-mapping.md#visualization)可以用於環境的即時意見反應，但在許多情況下，平面和防水物件的簡單性可提供更高的效能或視覺品質。</span><span class="sxs-lookup"><span data-stu-id="79bd6-160">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="79bd6-161">如果投影在四邊形或平面防水網格所提供的平面表面上，使用空間對應所描述的陰影投射和接地技術可能會更滿意。</span><span class="sxs-lookup"><span data-stu-id="79bd6-161">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="79bd6-162">這特別適用于透過預先掃描不是最佳的環境/案例，因為場景會推斷，而完成環境和平面假設會將成品降至最低。</span><span class="sxs-lookup"><span data-stu-id="79bd6-162">This is especially true for environments/scenarios where through pre-scanning is not optimal due to the fact that the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="79bd6-163">此外，空間對應所傳回的表面總數會受到內部空間快取的限制，而場景理解的空間對應網格版本則能夠存取未快取的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="79bd6-163">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh is able to access spatial mapping data that is not cached.</span></span> <span data-ttu-id="79bd6-164">因此，場景理解較適合用來針對視覺效果或進一步的網格處理來捕獲較大空間的網格標記法（例如，大於單一房間）。</span><span class="sxs-lookup"><span data-stu-id="79bd6-164">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="79bd6-165">以 EnableWorldMesh 傳回的世界網格會在整個中具有一致的詳細資料層級，如果轉譯為線框，這可能會產生更令人滿意的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="79bd6-165">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="79bd6-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="79bd6-166">See Also</span></span>

* [<span data-ttu-id="79bd6-167">場景理解 SDK</span><span class="sxs-lookup"><span data-stu-id="79bd6-167">Scene understanding SDK</span></span>](scene-understanding-SDK.md)
* [<span data-ttu-id="79bd6-168">空間對應</span><span class="sxs-lookup"><span data-stu-id="79bd6-168">Spatial mapping</span></span>](spatial-mapping.md)
