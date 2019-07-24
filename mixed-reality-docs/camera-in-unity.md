---
title: Unity 中的相機
description: 如何使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、全像攝影、全像投影、沉浸式、焦點、深度緩衝區、僅限方向、位置、不透明、透明、裁剪
ms.openlocfilehash: 3a9846242dd1709bcaf927d8ffae33862e96ecc8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522387"
---
# <a name="camera-in-unity"></a><span data-ttu-id="a323e-104">Unity 中的相機</span><span class="sxs-lookup"><span data-stu-id="a323e-104">Camera in Unity</span></span>

<span data-ttu-id="a323e-105">當您磨損混合現實耳機時, 它會成為您的全像攝影世界的中心。</span><span class="sxs-lookup"><span data-stu-id="a323e-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="a323e-106">Unity[攝影機](http://docs.unity3d.com/Manual/class-Camera.html)元件會自動處理 stereoscopic 轉譯, 並在您的專案已選取 [Windows Mixed reality] 做為裝置 (在其他設定中) 時, 遵循您的 head 移動和旋轉區段中的 [Windows Store Player 設定])。</span><span class="sxs-lookup"><span data-stu-id="a323e-106">The Unity [Camera](http://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and will follow your head movement and rotation when your project has "Virtual Reality Supported" selected with "Windows Mixed Reality" as the device (in the Other Settings section of the Windows Store Player Settings).</span></span> <span data-ttu-id="a323e-107">在舊版 Unity 中, 這可能會列為「Windows 全像」。</span><span class="sxs-lookup"><span data-stu-id="a323e-107">This may be listed as "Windows Holographic" in older versions of Unity.</span></span>

<span data-ttu-id="a323e-108">不過, 若要完全優化視覺品質和全息圖形的[穩定性](hologram-stability.md), 您應該設定以下所述的相機設定。</span><span class="sxs-lookup"><span data-stu-id="a323e-108">However, to fully optimize visual quality and [hologram stability](hologram-stability.md), you should set the camera settings described below.</span></span>

>[!NOTE]
><span data-ttu-id="a323e-109">這些設定必須套用至您應用程式的每個場景中的相機。</span><span class="sxs-lookup"><span data-stu-id="a323e-109">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="a323e-110">根據預設, 當您在 Unity 中建立新場景時, 它會在階層中包含主要相機 GameObject, 其中包含相機元件, 但未正確套用下列設定。</span><span class="sxs-lookup"><span data-stu-id="a323e-110">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="a323e-111">使用混合現實工具組 v2 進行自動場景和相機設定。</span><span class="sxs-lookup"><span data-stu-id="a323e-111">Automatic Scene and Camera Setup with Mixed Reality Toolkit v2.</span></span> 

<span data-ttu-id="a323e-112">遵循[逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)指南, 將混合現實工具組 v2 新增至您的 Unity 專案, 它會自動設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="a323e-112">Follow the [step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) guide to add Mixed Reality Toolkit v2 to your Unity project and it will configure your project automatically.</span></span>

<span data-ttu-id="a323e-113">您也可以使用下一節中的指南, 手動設定專案, 而不 MRTK。</span><span class="sxs-lookup"><span data-stu-id="a323e-113">You can also manually configure the project without MRTK with the guide in the section below.</span></span> 

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="a323e-114">全像沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="a323e-114">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="a323e-115">Unity 攝影機元件上的預設設定適用于傳統3D 應用程式, 需要 skybox 的背景, 因為它們沒有真實世界。</span><span class="sxs-lookup"><span data-stu-id="a323e-115">The default settings on the Unity Camera component are for traditional 3D applications which need a skybox-like background as they don't have a real world.</span></span>
* <span data-ttu-id="a323e-116">在 **[沉浸式耳機](immersive-headset-hardware-details.md)** 上執行時, 您會轉譯使用者看到的所有內容, 因此您可能會想要保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="a323e-116">When running on an **[immersive headset](immersive-headset-hardware-details.md)**, you are rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="a323e-117">不過, 在[HoloLens](hololens-hardware-details.md)這類全像的**耳機**上執行時, 真實世界應該會出現在相機呈現的所有內容背後。</span><span class="sxs-lookup"><span data-stu-id="a323e-117">However, when running on a **holographic headset** like [HoloLens](hololens-hardware-details.md), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="a323e-118">若要這麼做, 請將相機背景設定為透明 (在 HoloLens 中, 黑色呈現為透明), 而不是 Skybox 材質:</span><span class="sxs-lookup"><span data-stu-id="a323e-118">To do this, set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="a323e-119">在 [階層] 面板中選取主要相機</span><span class="sxs-lookup"><span data-stu-id="a323e-119">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="a323e-120">在 [偵測器] 面板中, 尋找相機元件, 並將 [清除旗標] 下拉式清單從 Skybox 變更為純色</span><span class="sxs-lookup"><span data-stu-id="a323e-120">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="a323e-121">選取背景色彩選擇器, 並將 RGBA 值變更為 (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="a323e-121">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="a323e-122">您可以使用腳本, 在執行時間判斷耳機是否為沉浸式或全像攝影, 方法是檢查[HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)。</span><span class="sxs-lookup"><span data-stu-id="a323e-122">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>


## <a name="positioning-the-camera"></a><span data-ttu-id="a323e-123">定位相機</span><span class="sxs-lookup"><span data-stu-id="a323e-123">Positioning the Camera</span></span>

<span data-ttu-id="a323e-124">如果您將使用者的開始位置想像為 (X:, 則可以更輕鬆地配置您的應用程式)。0、Y:0, Z:0)。</span><span class="sxs-lookup"><span data-stu-id="a323e-124">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="a323e-125">由於主要攝影機是追蹤使用者頭部的移動, 因此可以藉由設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="a323e-125">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="a323e-126">在 [階層] 面板中選取主要相機</span><span class="sxs-lookup"><span data-stu-id="a323e-126">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="a323e-127">在 偵測器 面板中, 尋找 轉換 元件, 並將位置從 (X:0、Y:1, Z:-10) 至 (X:0、Y:0, Z:0</span><span class="sxs-lookup"><span data-stu-id="a323e-127">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="a323e-128">![Unity 中的 [偵測器] 窗格中的相機](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="a323e-128">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span><br>
   <span data-ttu-id="a323e-129">*Unity 中的 [偵測器] 窗格中的相機*</span><span class="sxs-lookup"><span data-stu-id="a323e-129">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="a323e-130">剪輯平面</span><span class="sxs-lookup"><span data-stu-id="a323e-130">Clip planes</span></span>

<span data-ttu-id="a323e-131">太接近使用者的轉譯內容可能會令人混淆。</span><span class="sxs-lookup"><span data-stu-id="a323e-131">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="a323e-132">您可以調整相機元件上的[近距離剪輯平面](hologram-stability.md#hologram-render-distances)。</span><span class="sxs-lookup"><span data-stu-id="a323e-132">You can adjust the [near and far clip planes](hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>
1. <span data-ttu-id="a323e-133">在 [階層] 面板中選取主要相機</span><span class="sxs-lookup"><span data-stu-id="a323e-133">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="a323e-134">在 [偵測器] 面板中, 尋找相機元件裁剪平面, 並將近端 textbox 從0.3 變更為85。</span><span class="sxs-lookup"><span data-stu-id="a323e-134">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to .85.</span></span> <span data-ttu-id="a323e-135">呈現更接近的內容可能會導致使用者 discomfort, 而且應該根據轉譯[距離方針](hologram-stability.md#hologram-render-distances)來避免。</span><span class="sxs-lookup"><span data-stu-id="a323e-135">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="a323e-136">多個相機</span><span class="sxs-lookup"><span data-stu-id="a323e-136">Multiple Cameras</span></span>

<span data-ttu-id="a323e-137">當場景中有多個相機元件時, Unity 會藉由檢查哪個 GameObject 具有 MainCamera 標籤, 來知道要使用哪一個相機來 stereoscopic 轉譯和 head 追蹤。</span><span class="sxs-lookup"><span data-stu-id="a323e-137">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking by checking which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="a323e-138">Recentering 上一位經驗</span><span class="sxs-lookup"><span data-stu-id="a323e-138">Recentering a seated experience</span></span>

<span data-ttu-id="a323e-139">如果您要建立[大規模的經驗](coordinate-systems.md), 您可以呼叫 XR, 在使用者目前的前端位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="a323e-139">If you're building a [seated-scale experience](coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="a323e-140">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="a323e-140">Reprojection modes</span></span>

<span data-ttu-id="a323e-141">HoloLens 和沉浸式耳機都會 reproject 應用程式轉譯的每個畫面格, 以便在發出光子時, 針對使用者的實際標頭位置 misprediction 進行調整。</span><span class="sxs-lookup"><span data-stu-id="a323e-141">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="a323e-142">預設:</span><span class="sxs-lookup"><span data-stu-id="a323e-142">By default:</span></span>

* <span data-ttu-id="a323e-143">如果應用程式提供特定框架的深度緩衝區, 則**沉浸式耳機**會執行位置 reprojection、調整您的全像位置和方向 misprediction 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="a323e-143">**Immersive headsets** will perform positional reprojection, adjusting your holograms for misprediction in both position and orientation, if the app provides a depth buffer for a given frame.</span></span>  <span data-ttu-id="a323e-144">如果未提供深度緩衝區, 系統只會在方向更正 mispredictions。</span><span class="sxs-lookup"><span data-stu-id="a323e-144">If a depth buffer is not provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="a323e-145">如 HoloLens 這類全像的**耳機**將會執行位置 reprojection, 不論應用程式是否提供其深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a323e-145">**Holographic headsets** like HoloLens will perform positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="a323e-146">在 HoloLens 上可能沒有深度緩衝區, 因為轉譯通常是以真實世界提供的穩定背景來進行稀疏。</span><span class="sxs-lookup"><span data-stu-id="a323e-146">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="a323e-147">如果您知道您要使用嚴格的主體鎖定內容來建立[僅限方向的體驗](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)(例如, 360 度的影片內容), 您可以將 reprojection 模式明確設定為僅透過設定[的方向。HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) To [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。</span><span class="sxs-lookup"><span data-stu-id="a323e-147">If you know that you are building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (e.g. 360-degree video content), you can explicitly set the reprojection mode to be orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="a323e-148">與 Windows 共用深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="a323e-148">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="a323e-149">將應用程式的深度緩衝區與 Windows 共用, 每個畫面格都會根據您要轉譯的頭戴式裝置類型, 為您的應用程式提供兩種影像的其中一種提升:</span><span class="sxs-lookup"><span data-stu-id="a323e-149">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>
* <span data-ttu-id="a323e-150">當提供深度緩衝區時,**沉浸式耳機**可以執行位置 reprojection, 調整您的全像位置和方向 misprediction 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="a323e-150">**Immersive headsets** can perform positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="a323e-151">在提供深度緩衝區時, 像是 HoloLens 這類全像攝影的**耳機**會自動選取[焦點](focus-point-in-unity.md), 並在與大部分內容相交的平面上優化全息影像的穩定性。</span><span class="sxs-lookup"><span data-stu-id="a323e-151">**Holographic headsets** like HoloLens will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span>

<span data-ttu-id="a323e-152">若要設定您的 Unity 應用程式是否會提供深度緩衝區給 Windows:</span><span class="sxs-lookup"><span data-stu-id="a323e-152">To set whether your Unity app will provide a depth buffer to Windows:</span></span>
1. <span data-ttu-id="a323e-153">移至 **[編輯** > **專案設定** > ] [**播放** > **通用 Windows 平臺]**  > 索引標籤**XR 設定**。</span><span class="sxs-lookup"><span data-stu-id="a323e-153">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="a323e-154">展開 [ **Windows Mixed REALITY SDK** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="a323e-154">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="a323e-155">勾選或取消核取 [**啟用深度緩衝區共用**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a323e-155">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="a323e-156">預設會在建立的新專案中核取此功能, 因為這項功能已新增至 Unity, 而且預設會針對已升級的舊版專案取消選取。</span><span class="sxs-lookup"><span data-stu-id="a323e-156">This will be checked by default in new projects created since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="a323e-157">只要 Windows 能夠精確地將深度緩衝區中正規化的每圖元深度值對應到量表中的距離, 並使用您在主攝影機上的 Unity 中所設定的近和遠平面, 就能為 Windows 提供深度緩衝區來改善視覺品質。</span><span class="sxs-lookup"><span data-stu-id="a323e-157">Providing a depth buffer to Windows can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="a323e-158">如果您的轉譯行程以一般方式處理深度值, 您通常應該會在這裡正常運作, 但在顯示到現有的色彩圖元時, 寫入深度緩衝區的半透明轉譯傳遞可能會使 reprojection 混淆。</span><span class="sxs-lookup"><span data-stu-id="a323e-158">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="a323e-159">如果您知道您的轉譯行程會讓許多最後深度的圖元變得不正確, 您可能會取消核取 [啟用深度緩衝區共用], 以取得更佳的視覺品質。</span><span class="sxs-lookup"><span data-stu-id="a323e-159">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>


## <a name="see-also"></a><span data-ttu-id="a323e-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a323e-160">See also</span></span>
* [<span data-ttu-id="a323e-161">全像投影穩定性</span><span class="sxs-lookup"><span data-stu-id="a323e-161">Hologram stability</span></span>](hologram-stability.md)
* [<span data-ttu-id="a323e-162">MixedRealityToolkit 主要攝影機 prefab</span><span class="sxs-lookup"><span data-stu-id="a323e-162">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
