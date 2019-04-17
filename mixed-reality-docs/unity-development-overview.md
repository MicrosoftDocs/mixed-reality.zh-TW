---
title: Unity 開發概觀
description: 取得開始的建置混合實境應用程式，在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，混合實境、 開發、 開始、 新的專案、 移植、 功能、 相機、 模擬、 模擬、 文件
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596903"
---
# <a name="unity-development-overview"></a><span data-ttu-id="cabad-104">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="cabad-104">Unity development overview</span></span>

<span data-ttu-id="cabad-105">建置的最快路徑[mixed 的 reality 應用程式](app-views.md)是具有[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="cabad-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="cabad-106">我們建議您花時間來探索[Unity 教學課程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="cabad-106">We recommend you take the time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="cabad-107">如果您需要的資產，Unity 的全方位[Asset Store](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="cabad-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="cabad-108">一旦您已經建立基本的了解的 Unity，您可以瀏覽[混合實境 Academy](academy.md)若要了解使用 Unity 的混合的實境開發的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cabad-108">Once you have built up a basic understanding of Unity, you can visit the [Mixed Reality Academy](academy.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="cabad-109">請造訪[Unity 混合實境論壇](http://forum.unity3d.com/forums/hololens.102/)來參與社群建置 Unity 中的混合的實境應用程式的其餘部分，並尋找您可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="cabad-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="cabad-110">移植到 Windows 混和實境現有的 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="cabad-110">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="cabad-111">如果您有現有的 Unity 專案，您要移植到 Windows 混和實境，遵循[Unity 移植指南](porting-guides.md)開始著手。</span><span class="sxs-lookup"><span data-stu-id="cabad-111">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="cabad-112">設定新的 Unity 專案的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cabad-112">Configuring a new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="cabad-113">若要開始建置使用 Unity 的混合的實境應用程式第一次[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="cabad-113">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> <span data-ttu-id="cabad-114">如果您將目標 Windows Mixed Reality 沈浸式耳機，而不是 HoloLens，您將需要 Unity 的特殊版本現在。</span><span class="sxs-lookup"><span data-stu-id="cabad-114">If you'll be targeting Windows Mixed Reality immersive headsets rather than HoloLens, you'll need a special version of Unity for now.</span></span>

<span data-ttu-id="cabad-115">如果您剛建立新的 Unity 專案有較少的 Unity 設定您要變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="cabad-115">If you've just created a new Unity project, there are a small set of Unity settings you'll need to change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

### <a name="per-project-settings"></a><span data-ttu-id="cabad-116">每個專案設定</span><span class="sxs-lookup"><span data-stu-id="cabad-116">Per-project settings</span></span>

<span data-ttu-id="cabad-117">若要目標 Windows Mixed Reality，必須先設定您的 Unity 專案，以匯出為通用 Windows 平台應用程式：</span><span class="sxs-lookup"><span data-stu-id="cabad-117">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="cabad-118">選取**檔案 > 組建設定...**</span><span class="sxs-lookup"><span data-stu-id="cabad-118">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="cabad-119">選取 **通用 Windows 平台**平台清單，然後按一下**切換平台**</span><span class="sxs-lookup"><span data-stu-id="cabad-119">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="cabad-120">設定**SDK**到**通用 10**</span><span class="sxs-lookup"><span data-stu-id="cabad-120">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="cabad-121">設定**目標裝置**要**任何裝置**支援沈浸式耳機或切換至**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="cabad-121">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="cabad-122">設定**建置型別**到**D3D**</span><span class="sxs-lookup"><span data-stu-id="cabad-122">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="cabad-123">設定**UWP SDK**到**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="cabad-123">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="cabad-124">我們再需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。</span><span class="sxs-lookup"><span data-stu-id="cabad-124">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="cabad-125">我們的做法是啟用 「 虛擬實境支援 」:</span><span class="sxs-lookup"><span data-stu-id="cabad-125">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="cabad-126">從**組建設定...** 視窗中，開啟**播放程式設定...**</span><span class="sxs-lookup"><span data-stu-id="cabad-126">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="cabad-127">選取 [**通用 Windows 平台設定**] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="cabad-127">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="cabad-128">依序展開**XR 設定**群組</span><span class="sxs-lookup"><span data-stu-id="cabad-128">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="cabad-129">在  **XR 設定**區段中，按一下**受支援的虛擬實境**核取方塊以新增**虛擬實境裝置**清單。</span><span class="sxs-lookup"><span data-stu-id="cabad-129">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="cabad-130">在  **XR 設定**群組中，確認 **「 Windows Mixed Reality"** 列為支援的裝置。</span><span class="sxs-lookup"><span data-stu-id="cabad-130">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="cabad-131">（這可能會顯示為 「 Windows 全像 」 在較舊版本的 Unity）</span><span class="sxs-lookup"><span data-stu-id="cabad-131">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="cabad-132">您的應用程式現在可以進行基本全像攝影版的轉譯和空間的輸入。</span><span class="sxs-lookup"><span data-stu-id="cabad-132">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="cabad-133">若要更進一步，並利用特定功能，您的應用程式必須宣告適當的功能資訊清單中。</span><span class="sxs-lookup"><span data-stu-id="cabad-133">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="cabad-134">可以在 Unity 中進行資訊清單宣告，因此它們會包含在每個後續的專案匯入。</span><span class="sxs-lookup"><span data-stu-id="cabad-134">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="cabad-135">設定位於**Player 設定 > 適用於通用 Windows 平台的設定 > 發行設定 > 功能**。</span><span class="sxs-lookup"><span data-stu-id="cabad-135">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="cabad-136">啟用常用 Unity Api for Mixed Reality 適用的功能如下：</span><span class="sxs-lookup"><span data-stu-id="cabad-136">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="cabad-137">功能</span><span class="sxs-lookup"><span data-stu-id="cabad-137">Capability</span></span>  |  <span data-ttu-id="cabad-138">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="cabad-138">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="cabad-139">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="cabad-139">SpatialPerception</span></span>  |  <span data-ttu-id="cabad-140">SurfaceObserver (存取權[空間的對應](spatial-mapping.md)網狀結構 HoloLens 上)&mdash;*沒有一般的耳機空間追蹤您所需的功能*</span><span class="sxs-lookup"><span data-stu-id="cabad-140">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="cabad-141">WebCam</span><span class="sxs-lookup"><span data-stu-id="cabad-141">WebCam</span></span>  |  <span data-ttu-id="cabad-142">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="cabad-142">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="cabad-143">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="cabad-143">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="cabad-144">PhotoCapture 或 VideoCapture，分別 （儲存時所擷取的內容）</span><span class="sxs-lookup"><span data-stu-id="cabad-144">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="cabad-145">麥克風</span><span class="sxs-lookup"><span data-stu-id="cabad-145">Microphone</span></span>  |  <span data-ttu-id="cabad-146">VideoCapture （當擷取音訊）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="cabad-146">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="cabad-147">InternetClient</span><span class="sxs-lookup"><span data-stu-id="cabad-147">InternetClient</span></span>  |  <span data-ttu-id="cabad-148">DictationRecognizer （以及使用 Unity Profiler）</span><span class="sxs-lookup"><span data-stu-id="cabad-148">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="cabad-149">**Unity 的品質設定**</span><span class="sxs-lookup"><span data-stu-id="cabad-149">**Unity quality settings**</span></span>

<span data-ttu-id="cabad-150">![Unity 的品質設定](images/unityqualitysettings-350px.png)</span><span class="sxs-lookup"><span data-stu-id="cabad-150">![Unity quality settings](images/unityqualitysettings-350px.png)</span></span><br>
<span data-ttu-id="cabad-151">*Unity 的品質設定*</span><span class="sxs-lookup"><span data-stu-id="cabad-151">*Unity quality settings*</span></span>

<span data-ttu-id="cabad-152">HoloLens 有 mobile 類別的 GPU。</span><span class="sxs-lookup"><span data-stu-id="cabad-152">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="cabad-153">如果您的應用程式的目標 HoloLens，您會想的品質設定為最快的效能微調請確定我們會保留完整的畫面播放速率：</span><span class="sxs-lookup"><span data-stu-id="cabad-153">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="cabad-154">選取**編輯 > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="cabad-154">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="cabad-155">選取**下拉式清單**下方**Windows 市集**標誌，然後選取**Fastest**。</span><span class="sxs-lookup"><span data-stu-id="cabad-155">Select the **dropdown** under the **Windows Store** logo and select **Fastest**.</span></span> <span data-ttu-id="cabad-156">您知道設定正確時套用的 Windows 市集的資料行中的方塊並**最快**資料列是綠色。</span><span class="sxs-lookup"><span data-stu-id="cabad-156">You'll know the setting is applied correctly when the box in the Windows Store column and **Fastest** row is green.</span></span>

### <a name="per-scene-settings"></a><span data-ttu-id="cabad-157">每個場景設定</span><span class="sxs-lookup"><span data-stu-id="cabad-157">Per-scene settings</span></span>

<span data-ttu-id="cabad-158">**Unity 觀景窗設定**</span><span class="sxs-lookup"><span data-stu-id="cabad-158">**Unity camera settings**</span></span>

<span data-ttu-id="cabad-159">![Unity 觀景窗設定](images/unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="cabad-159">![Unity camera settings](images/unitycamerasettings.png)</span></span><br>
<span data-ttu-id="cabad-160">*Unity 觀景窗設定*</span><span class="sxs-lookup"><span data-stu-id="cabad-160">*Unity camera settings*</span></span>

<span data-ttu-id="cabad-161">一旦您啟用 「 虛擬實境支援 」 核取方塊[Unity 數位相機](camera-in-unity.md)元件控制代碼[前端追蹤和立體視覺呈現](rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="cabad-161">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="cabad-162">就不需要將它取代自訂的數位相機，若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="cabad-162">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="cabad-163">如果您的應用程式的目標 HoloLens 具體來說，有一些需要變更以最佳化裝置透明的顯示畫面，讓您的應用程式就會直接透過真實世界的設定：</span><span class="sxs-lookup"><span data-stu-id="cabad-163">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="cabad-164">在 **階層**，選取**Main Camera**</span><span class="sxs-lookup"><span data-stu-id="cabad-164">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="cabad-165">在**Inspector**  面板中，設定轉換**位置**來**0，0，0**讓使用者標頭的位置啟動 Unity 世界原始位置。</span><span class="sxs-lookup"><span data-stu-id="cabad-165">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="cabad-166">變更**清除旗標**要**單色**。</span><span class="sxs-lookup"><span data-stu-id="cabad-166">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="cabad-167">變更**背景**色彩**RGBA 0,0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="cabad-167">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="cabad-168">黑色呈現為透明的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="cabad-168">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="cabad-169">變更**接近裁剪平面-** 要[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （公尺）。</span><span class="sxs-lookup"><span data-stu-id="cabad-169">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="cabad-170">如果您刪除，然後建立新的相機，請確定您的相機**標籤**作為**MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="cabad-170">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="cabad-171">新增混合的實境功能和輸入</span><span class="sxs-lookup"><span data-stu-id="cabad-171">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="cabad-172">一旦您已設定您的專案，如上面所述，標準的 Unity 遊戲物件 （例如數位相機） 則受到立即的**安插擴展經驗**，與自動更新使用者的相機的位置移動透過世界其標頭。</span><span class="sxs-lookup"><span data-stu-id="cabad-172">Once you've configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="cabad-173">新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)，[筆勢，移動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)透過直接內建的 ApiUnity。</span><span class="sxs-lookup"><span data-stu-id="cabad-173">Adding support for Windows Mixed Reality features such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span>

<span data-ttu-id="cabad-174">您的第一個步驟應該是檢閱[體驗標尺](coordinate-systems.md)為目標應用程式：</span><span class="sxs-lookup"><span data-stu-id="cabad-174">Your first step should be to review the [experience scales](coordinate-systems.md) that your app can target:</span></span>
* <span data-ttu-id="cabad-175">如果您想要建置**方向專用**或**插入擴充槽擴展經驗**，您將需要設定 Unity 的追蹤要空間型別[「 定態](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="cabad-175">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="cabad-176">如果您想要建置**常設級別**或**聊天室擴展經驗**，您必須確保 Unity 的追蹤空間型別已成功設定為[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="cabad-176">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="cabad-177">如果您想要建置**全球級別**體驗 HoloLens，讓使用者漫遊遠 5 公尺之外，您必須使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)元件。</span><span class="sxs-lookup"><span data-stu-id="cabad-177">If you're looking to build a **world-scale** experience on HoloLens, letting users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="cabad-178">所有的核心建置組塊，混合的實境應用程式中與其他的 Unity Api 一致的方式公開：</span><span class="sxs-lookup"><span data-stu-id="cabad-178">All of the core building blocks for mixed reality apps are exposed in a manner consistent with other Unity APIs:</span></span>
* [<span data-ttu-id="cabad-179">相機</span><span class="sxs-lookup"><span data-stu-id="cabad-179">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="cabad-180">座標系統</span><span class="sxs-lookup"><span data-stu-id="cabad-180">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="cabad-181">Gaze</span><span class="sxs-lookup"><span data-stu-id="cabad-181">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="cabad-182">筆勢和動作控制站</span><span class="sxs-lookup"><span data-stu-id="cabad-182">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="cabad-183">語音輸入</span><span class="sxs-lookup"><span data-stu-id="cabad-183">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="cabad-184">持續性</span><span class="sxs-lookup"><span data-stu-id="cabad-184">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="cabad-185">空間的音效</span><span class="sxs-lookup"><span data-stu-id="cabad-185">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="cabad-186">空間對應</span><span class="sxs-lookup"><span data-stu-id="cabad-186">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="cabad-187">有許多的混合的實境應用程式將會想使用的也會公開給 Unity 應用程式的其他重要功能：</span><span class="sxs-lookup"><span data-stu-id="cabad-187">There are other key features that many mixed reality apps will want to use, which are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="cabad-188">共用的體驗</span><span class="sxs-lookup"><span data-stu-id="cabad-188">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="cabad-189">之外的可尋獲相機</span><span class="sxs-lookup"><span data-stu-id="cabad-189">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="cabad-190">焦點</span><span class="sxs-lookup"><span data-stu-id="cabad-190">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="cabad-191">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="cabad-191">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="cabad-192">鍵盤</span><span class="sxs-lookup"><span data-stu-id="cabad-192">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="cabad-193">真實或模擬裝置上執行您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="cabad-193">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="cabad-194">您有全像攝影版的 Unity 專案準備好測試，您下一步是要[匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="cabad-194">Once you've got your holographic Unity project ready to test out, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="cabad-195">之後，在 VS 方案，您可以再執行您的應用程式其中一種方式，使用真實或模擬的裝置：</span><span class="sxs-lookup"><span data-stu-id="cabad-195">With that VS solution in hand, you can then run your app in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="cabad-196">將部署到實際的 HoloLens 或 Windows Mixed Reality 沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="cabad-196">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="cabad-197">部署至 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="cabad-197">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="cabad-198">將部署到 Windows Mixed Reality 沈浸式耳機模擬器</span><span class="sxs-lookup"><span data-stu-id="cabad-198">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="cabad-199">Unity 文件</span><span class="sxs-lookup"><span data-stu-id="cabad-199">Unity documentation</span></span>

<span data-ttu-id="cabad-200">除了本文件中可以使用 Windows 開發人員中心上，Unity 會安裝 Windows Mixed Reality 功能與 Unity Editor 中的文件。</span><span class="sxs-lookup"><span data-stu-id="cabad-200">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="cabad-201">Unity 提供文件包含兩個不同的區段：</span><span class="sxs-lookup"><span data-stu-id="cabad-201">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="cabad-202">**Unity 指令碼參考**</span><span class="sxs-lookup"><span data-stu-id="cabad-202">**Unity scripting reference**</span></span>
    * <span data-ttu-id="cabad-203">本節的文件包含 Unity 所提供的指令碼 api 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cabad-203">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="cabad-204">可透過從 Unity 編輯器**協助 > 指令碼參考**</span><span class="sxs-lookup"><span data-stu-id="cabad-204">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="cabad-205">**Unity manual**</span><span class="sxs-lookup"><span data-stu-id="cabad-205">**Unity manual**</span></span>
    * <span data-ttu-id="cabad-206">本手冊可協助您了解如何使用 Unity 中，從基本到進階技術。</span><span class="sxs-lookup"><span data-stu-id="cabad-206">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="cabad-207">可透過從 Unity 編輯器**協助 > 手動**</span><span class="sxs-lookup"><span data-stu-id="cabad-207">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="cabad-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cabad-208">See also</span></span>
* [<span data-ttu-id="cabad-209">MR 基本概念 100:開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="cabad-209">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="cabad-210">Unity 的建議的設定</span><span class="sxs-lookup"><span data-stu-id="cabad-210">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="cabad-211">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="cabad-211">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="cabad-212">匯出和建置 Unity Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="cabad-212">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="cabad-213">HoloLens 與 Unity 應用程式使用的 Windows 命名空間</span><span class="sxs-lookup"><span data-stu-id="cabad-213">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="cabad-214">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="cabad-214">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="cabad-215">Unity 遊戲模式</span><span class="sxs-lookup"><span data-stu-id="cabad-215">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="cabad-216">移植指南</span><span class="sxs-lookup"><span data-stu-id="cabad-216">Porting guides</span></span>](porting-guides.md)
