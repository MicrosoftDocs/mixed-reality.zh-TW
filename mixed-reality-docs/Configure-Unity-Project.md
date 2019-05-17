---
title: 為 Windows Mixed Reality 設定新的 Unity 專案
description: 設定無 MRTK 的 Unity 專案
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合實境，開發、 開始，新的專案
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993543"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="ace8d-104">為 Windows Mixed Reality 設定新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ace8d-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="ace8d-105">（如果您已經為您的 Unity 專案匯入 MRTK v2 略過）</span><span class="sxs-lookup"><span data-stu-id="ace8d-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="ace8d-106">如果您想要建立新的 Unity 專案，但不匯入混合實境工具組，有較少的 Unity 設定，您必須手動變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="ace8d-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="ace8d-107">每個專案設定</span><span class="sxs-lookup"><span data-stu-id="ace8d-107">Per-project settings</span></span>

<span data-ttu-id="ace8d-108">若要目標 Windows Mixed Reality，必須先設定您的 Unity 專案，以匯出為通用 Windows 平台應用程式：</span><span class="sxs-lookup"><span data-stu-id="ace8d-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="ace8d-109">選取**檔案 > 組建設定...**</span><span class="sxs-lookup"><span data-stu-id="ace8d-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="ace8d-110">選取 **通用 Windows 平台**平台清單，然後按一下**切換平台**</span><span class="sxs-lookup"><span data-stu-id="ace8d-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="ace8d-111">設定**SDK**到**通用 10**</span><span class="sxs-lookup"><span data-stu-id="ace8d-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="ace8d-112">設定**目標裝置**要**任何裝置**支援沈浸式耳機或切換至**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ace8d-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="ace8d-113">設定**建置型別**到**D3D**</span><span class="sxs-lookup"><span data-stu-id="ace8d-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="ace8d-114">設定**UWP SDK**到**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="ace8d-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="ace8d-115">我們再需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。</span><span class="sxs-lookup"><span data-stu-id="ace8d-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="ace8d-116">我們的做法是啟用 「 虛擬實境支援 」:</span><span class="sxs-lookup"><span data-stu-id="ace8d-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="ace8d-117">從**組建設定...** 視窗中，開啟**播放程式設定...**</span><span class="sxs-lookup"><span data-stu-id="ace8d-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="ace8d-118">選取 [**通用 Windows 平台設定**] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="ace8d-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="ace8d-119">依序展開**XR 設定**群組</span><span class="sxs-lookup"><span data-stu-id="ace8d-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="ace8d-120">在  **XR 設定**區段中，按一下**受支援的虛擬實境**核取方塊以新增**虛擬實境裝置**清單。</span><span class="sxs-lookup"><span data-stu-id="ace8d-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="ace8d-121">在  **XR 設定**群組中，確認 **「 Windows Mixed Reality"** 列為支援的裝置。</span><span class="sxs-lookup"><span data-stu-id="ace8d-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="ace8d-122">（這可能會顯示為 「 Windows 全像 」 在較舊版本的 Unity）</span><span class="sxs-lookup"><span data-stu-id="ace8d-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="ace8d-123">您的應用程式現在可以進行基本全像攝影版的轉譯和空間的輸入。</span><span class="sxs-lookup"><span data-stu-id="ace8d-123">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="ace8d-124">若要更進一步，並利用特定功能，您的應用程式必須宣告適當的功能資訊清單中。</span><span class="sxs-lookup"><span data-stu-id="ace8d-124">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="ace8d-125">可以在 Unity 中進行資訊清單宣告，因此它們會包含在每個後續的專案匯入。</span><span class="sxs-lookup"><span data-stu-id="ace8d-125">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="ace8d-126">設定位於**Player 設定 > 適用於通用 Windows 平台的設定 > 發行設定 > 功能**。</span><span class="sxs-lookup"><span data-stu-id="ace8d-126">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="ace8d-127">啟用常用 Unity Api for Mixed Reality 適用的功能如下：</span><span class="sxs-lookup"><span data-stu-id="ace8d-127">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="ace8d-128">功能</span><span class="sxs-lookup"><span data-stu-id="ace8d-128">Capability</span></span>  |  <span data-ttu-id="ace8d-129">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="ace8d-129">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="ace8d-130">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="ace8d-130">SpatialPerception</span></span>  |  <span data-ttu-id="ace8d-131">SurfaceObserver (存取權[空間的對應](spatial-mapping.md)網狀結構 HoloLens 上)&mdash;*沒有一般的耳機空間追蹤您所需的功能*</span><span class="sxs-lookup"><span data-stu-id="ace8d-131">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="ace8d-132">WebCam</span><span class="sxs-lookup"><span data-stu-id="ace8d-132">WebCam</span></span>  |  <span data-ttu-id="ace8d-133">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="ace8d-133">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="ace8d-134">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="ace8d-134">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="ace8d-135">PhotoCapture 或 VideoCapture，分別 （儲存時所擷取的內容）</span><span class="sxs-lookup"><span data-stu-id="ace8d-135">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="ace8d-136">麥克風</span><span class="sxs-lookup"><span data-stu-id="ace8d-136">Microphone</span></span>  |  <span data-ttu-id="ace8d-137">VideoCapture （當擷取音訊）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="ace8d-137">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="ace8d-138">InternetClient</span><span class="sxs-lookup"><span data-stu-id="ace8d-138">InternetClient</span></span>  |  <span data-ttu-id="ace8d-139">DictationRecognizer （以及使用 Unity Profiler）</span><span class="sxs-lookup"><span data-stu-id="ace8d-139">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="ace8d-140">**Unity 的品質設定**</span><span class="sxs-lookup"><span data-stu-id="ace8d-140">**Unity quality settings**</span></span>

<span data-ttu-id="ace8d-141">![Unity 的品質設定](images/unityqualitysettings-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ace8d-141">![Unity quality settings](images/unityqualitysettings-350px.png)</span></span><br>
<span data-ttu-id="ace8d-142">*Unity 的品質設定*</span><span class="sxs-lookup"><span data-stu-id="ace8d-142">*Unity quality settings*</span></span>

<span data-ttu-id="ace8d-143">HoloLens 有 mobile 類別的 GPU。</span><span class="sxs-lookup"><span data-stu-id="ace8d-143">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="ace8d-144">如果您的應用程式的目標 HoloLens，您會想的品質設定為最快的效能微調請確定我們會保留完整的畫面播放速率：</span><span class="sxs-lookup"><span data-stu-id="ace8d-144">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="ace8d-145">選取**編輯 > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="ace8d-145">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="ace8d-146">選取 **下拉式清單**下方**Windows 市集**標誌，然後選取**非常低**。</span><span class="sxs-lookup"><span data-stu-id="ace8d-146">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="ace8d-147">您知道設定正確時套用的 Windows 市集的資料行中的方塊並**非常低**資料列是綠色。</span><span class="sxs-lookup"><span data-stu-id="ace8d-147">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="ace8d-148">每個場景設定</span><span class="sxs-lookup"><span data-stu-id="ace8d-148">Per-scene settings</span></span>

<span data-ttu-id="ace8d-149">**Unity 觀景窗設定**</span><span class="sxs-lookup"><span data-stu-id="ace8d-149">**Unity camera settings**</span></span>

<span data-ttu-id="ace8d-150">![Unity 觀景窗設定](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="ace8d-150">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="ace8d-151">*Unity 觀景窗設定*</span><span class="sxs-lookup"><span data-stu-id="ace8d-151">*Unity camera settings*</span></span>

<span data-ttu-id="ace8d-152">一旦您啟用 「 虛擬實境支援 」 核取方塊[Unity 數位相機](camera-in-unity.md)元件控制代碼[前端追蹤和立體視覺呈現](rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="ace8d-152">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="ace8d-153">就不需要將它取代自訂的數位相機，若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="ace8d-153">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="ace8d-154">如果您的應用程式的目標 HoloLens 具體來說，有一些需要變更以最佳化裝置透明的顯示畫面，讓您的應用程式就會直接透過真實世界的設定：</span><span class="sxs-lookup"><span data-stu-id="ace8d-154">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="ace8d-155">在 **階層**，選取**Main Camera**</span><span class="sxs-lookup"><span data-stu-id="ace8d-155">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="ace8d-156">在**Inspector**  面板中，設定轉換**位置**來**0，0，0**讓使用者標頭的位置啟動 Unity 世界原始位置。</span><span class="sxs-lookup"><span data-stu-id="ace8d-156">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="ace8d-157">變更**清除旗標**要**單色**。</span><span class="sxs-lookup"><span data-stu-id="ace8d-157">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="ace8d-158">變更**背景**色彩**RGBA 0,0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="ace8d-158">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="ace8d-159">黑色呈現為透明的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ace8d-159">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="ace8d-160">變更**接近裁剪平面-** 要[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （公尺）。</span><span class="sxs-lookup"><span data-stu-id="ace8d-160">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="ace8d-161">如果您刪除，然後建立新的相機，請確定您的相機**標籤**作為**MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="ace8d-161">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="ace8d-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ace8d-162">See also</span></span>
* [<span data-ttu-id="ace8d-163">混合實境 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="ace8d-163">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="ace8d-164">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="ace8d-164">Unity Development Overview</span></span>](unity-development-overview.md)