---
title: 為 Windows Mixed Reality 設定新的 Unity 專案
description: 在不 MRTK 的情況下設定 Unity 專案
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合現實，開發，快速入門，新專案
ms.openlocfilehash: af30cf91eda1b654bea6048c34f63c61238626c7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437119"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="c67e4-104">為 Windows Mixed Reality 設定新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="c67e4-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="c67e4-105">（如果您已將 MRTK v2 匯入 Unity 專案，請略過）</span><span class="sxs-lookup"><span data-stu-id="c67e4-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="c67e4-106">如果您想要建立新的 Unity 專案，但未匯入 Mixed Reality 工具組，則需要針對 Windows Mixed Reality 手動變更的一小組 Unity 設定，分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="c67e4-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="c67e4-107">每個專案的設定</span><span class="sxs-lookup"><span data-stu-id="c67e4-107">Per-project settings</span></span>

<span data-ttu-id="c67e4-108">若要以 Windows Mixed Reality 為目標，您必須先將 Unity 專案設定為匯出為通用 Windows 平臺應用程式：</span><span class="sxs-lookup"><span data-stu-id="c67e4-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span> 
1. <span data-ttu-id="c67e4-109">選取 [檔案 **> 組建設定**...]</span><span class="sxs-lookup"><span data-stu-id="c67e4-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="c67e4-110">在 [平臺] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="c67e4-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="c67e4-111">將**SDK**設定為**通用 10**</span><span class="sxs-lookup"><span data-stu-id="c67e4-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="c67e4-112">將 [**目標裝置**] 設定為 [**任何裝置**] 以支援沉浸式耳機或切換至**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c67e4-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="c67e4-113">將**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="c67e4-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="c67e4-114">將**UWP SDK**設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="c67e4-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="c67e4-115">接著，我們需要讓 Unity 知道，我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="c67e4-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="c67e4-116">我們藉由啟用「支援虛擬實境」來執行此動作：</span><span class="sxs-lookup"><span data-stu-id="c67e4-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="c67e4-117">從 [**組建設定 ...** ] 視窗中，開啟 [**播放者設定**]。</span><span class="sxs-lookup"><span data-stu-id="c67e4-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="c67e4-118">選取 [**通用 Windows 平臺**] 索引標籤的設定</span><span class="sxs-lookup"><span data-stu-id="c67e4-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="c67e4-119">展開 [ **XR 設定**] 群組</span><span class="sxs-lookup"><span data-stu-id="c67e4-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="c67e4-120">在 [ **XR 設定**] 區段中，勾選 [**支援虛擬實境**] 核取方塊以新增**虛擬實境裝置**清單。</span><span class="sxs-lookup"><span data-stu-id="c67e4-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="c67e4-121">在 [ **XR 設定**] 群組中，確認 **[Windows Mixed Reality]** 已列為支援的裝置。</span><span class="sxs-lookup"><span data-stu-id="c67e4-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="c67e4-122">（在舊版 Unity 中，這可能會顯示為「Windows 全像」）</span><span class="sxs-lookup"><span data-stu-id="c67e4-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="c67e4-123">![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="c67e4-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="c67e4-124">*Unity xr 設定*</span><span class="sxs-lookup"><span data-stu-id="c67e4-124">*Unity xr settings*</span></span>

<span data-ttu-id="c67e4-125">您的應用程式現在可以執行基本的全像攝影轉譯和空間輸入。</span><span class="sxs-lookup"><span data-stu-id="c67e4-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="c67e4-126">若要進一步瞭解並利用特定功能，您的應用程式必須在其資訊清單中宣告適當的功能。</span><span class="sxs-lookup"><span data-stu-id="c67e4-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="c67e4-127">資訊清單宣告可在 Unity 中進行，使其包含在每個後續的專案匯出中。</span><span class="sxs-lookup"><span data-stu-id="c67e4-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="c67e4-128">**通用 Windows 平臺 > 發佈設定 > 功能的 [播放程式設定] > 設定**中，可以找到此設定。</span><span class="sxs-lookup"><span data-stu-id="c67e4-128">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="c67e4-129">針對混合式現實啟用常用 Unity Api 的適用功能包括：</span><span class="sxs-lookup"><span data-stu-id="c67e4-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="c67e4-130">功能</span><span class="sxs-lookup"><span data-stu-id="c67e4-130">Capability</span></span>  |  <span data-ttu-id="c67e4-131">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="c67e4-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="c67e4-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="c67e4-132">SpatialPerception</span></span>  |  <span data-ttu-id="c67e4-133">SurfaceObserver （在 HoloLens 上存取[空間對應](spatial-mapping.md)網格）&mdash;*耳機的一般空間追蹤所需的功能*</span><span class="sxs-lookup"><span data-stu-id="c67e4-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="c67e4-134">網路</span><span class="sxs-lookup"><span data-stu-id="c67e4-134">WebCam</span></span>  |  <span data-ttu-id="c67e4-135">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="c67e4-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="c67e4-136">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="c67e4-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="c67e4-137">PhotoCapture 或 VideoCapture，分別是（儲存已捕獲的內容時）</span><span class="sxs-lookup"><span data-stu-id="c67e4-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="c67e4-138">麥克風</span><span class="sxs-lookup"><span data-stu-id="c67e4-138">Microphone</span></span>  |  <span data-ttu-id="c67e4-139">VideoCapture （在捕獲音訊時）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="c67e4-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="c67e4-140">InternetClient</span><span class="sxs-lookup"><span data-stu-id="c67e4-140">InternetClient</span></span>  |  <span data-ttu-id="c67e4-141">DictationRecognizer （並使用 Unity Profiler）</span><span class="sxs-lookup"><span data-stu-id="c67e4-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="c67e4-142">**Unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="c67e4-142">**Unity quality settings**</span></span>

<span data-ttu-id="c67e4-143">![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="c67e4-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="c67e4-144">*Unity 品質設定*</span><span class="sxs-lookup"><span data-stu-id="c67e4-144">*Unity quality settings*</span></span>

<span data-ttu-id="c67e4-145">HoloLens 具有行動類別 GPU。</span><span class="sxs-lookup"><span data-stu-id="c67e4-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="c67e4-146">如果您的應用程式是以 HoloLens 為目標，您會想要調整品質設定以取得最快的效能，以確保我們維持完整的畫面播放速率：</span><span class="sxs-lookup"><span data-stu-id="c67e4-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="c67e4-147">選取 [**編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="c67e4-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="c67e4-148">選取 [ **Windows Store** ] 標誌底下的**下拉式清單**，然後選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="c67e4-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="c67e4-149">當 [Windows Store] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。</span><span class="sxs-lookup"><span data-stu-id="c67e4-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="c67e4-150">每場景設定</span><span class="sxs-lookup"><span data-stu-id="c67e4-150">Per-scene settings</span></span>

<span data-ttu-id="c67e4-151">**Unity 攝影機設定**</span><span class="sxs-lookup"><span data-stu-id="c67e4-151">**Unity camera settings**</span></span>

<span data-ttu-id="c67e4-152">![Unity 攝影機設定](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="c67e4-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="c67e4-153">*Unity 攝影機設定*</span><span class="sxs-lookup"><span data-stu-id="c67e4-153">*Unity camera settings*</span></span>

<span data-ttu-id="c67e4-154">一旦您啟用 [支援虛擬實境] 核取方塊， [Unity 攝影機](camera-in-unity.md)元件就會處理[head 追蹤和 stereoscopic](rendering.md)轉譯。</span><span class="sxs-lookup"><span data-stu-id="c67e4-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="c67e4-155">您不需要將它取代為自訂相機來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="c67e4-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="c67e4-156">如果您的應用程式特別以 HoloLens 為目標，則需要變更幾個設定，以優化裝置的透明顯示，讓您的應用程式會向實體世界顯示：</span><span class="sxs-lookup"><span data-stu-id="c67e4-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="c67e4-157">**在階層中，選取** **主要相機**</span><span class="sxs-lookup"><span data-stu-id="c67e4-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="c67e4-158">在 [偵測**器**] 面板中，將 [轉換**位置**] 設定為**0，0，0，** 讓使用者標頭的位置從 Unity world 來源開始。</span><span class="sxs-lookup"><span data-stu-id="c67e4-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="c67e4-159">將 [**清除旗標**] 變更為**純色**。</span><span class="sxs-lookup"><span data-stu-id="c67e4-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="c67e4-160">將**背景**色彩變更為**RGBA 0，0，0**，0。</span><span class="sxs-lookup"><span data-stu-id="c67e4-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="c67e4-161">在 HoloLens 中，黑色呈現為透明。</span><span class="sxs-lookup"><span data-stu-id="c67e4-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="c67e4-162">變更**裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （計量）。</span><span class="sxs-lookup"><span data-stu-id="c67e4-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="c67e4-163">如果您刪除並建立新的相機，請確定您的相機已**標記**為**MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="c67e4-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="c67e4-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="c67e4-164">See also</span></span>
* [<span data-ttu-id="c67e4-165">混合現實工具組 v2</span><span class="sxs-lookup"><span data-stu-id="c67e4-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="c67e4-166">Unity 開發總覽</span><span class="sxs-lookup"><span data-stu-id="c67e4-166">Unity Development Overview</span></span>](unity-development-overview.md)
