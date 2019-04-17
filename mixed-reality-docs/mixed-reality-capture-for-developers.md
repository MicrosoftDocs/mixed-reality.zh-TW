---
title: 混合實境擷取適用於開發人員
description: 適用於開發人員，擷取的混合實境的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 相片、 視訊、 擷取、 相機
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591595"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="c4dc9-104">混合實境擷取適用於開發人員</span><span class="sxs-lookup"><span data-stu-id="c4dc9-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="c4dc9-105">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span> 

<span data-ttu-id="c4dc9-106">請參閱[應用程式中的啟用 MRC](#enabling-mrc-in-your-app)以下新的 MRC 功能有關的 HoloLens 2 指導方針。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-106">See [Enabling MRC in your app](#enabling-mrc-in-your-app) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="c4dc9-107">因為使用者無法接管[混合實境擷取](mixed-reality-capture.md)(MRC) 相片或視訊在任何時間，有幾件事開發您的應用程式時，您應該謹記在心。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-107">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="c4dc9-108">這包括 MRC 視覺品質和正在回應系統的變更，正在擷取 MRCs 時的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-108">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="c4dc9-109">開發人員可以也會順暢地整合混合的實境擷取和插入自己的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-109">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="c4dc9-110">MRC HoloLens （第一代） 上的支援視訊和相片最多 720p，雖然 MRC HoloLens 2 上的啟動支援高達 1080p 和相片的影片，4k 解析度。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-110">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="c4dc9-111">品質 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="c4dc9-111">The importance of quality MRC</span></span>

<span data-ttu-id="c4dc9-112">混合的實境擷取相片和影片可能是使用者會有您的應用程式的第一次。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-112">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="c4dc9-113">是否為您的 Microsoft Store 頁面上，或從共用 MRCs 社交網路上其他使用者的混合的實境螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-113">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="c4dc9-114">您可以使用 MRC 來示範您的應用程式，所以請教導使用者，鼓勵使用者共用其混合的環境的互動，以及根據使用者研究和解決問題。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-114">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="c4dc9-115">MRC 會如何影響您的應用程式</span><span class="sxs-lookup"><span data-stu-id="c4dc9-115">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="c4dc9-116">應用程式中啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="c4dc9-116">Enabling MRC in your app</span></span>

<span data-ttu-id="c4dc9-117">根據預設，應用程式並沒有採取任何動作，讓使用者可以採取混合的實境擷取。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-117">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span> <span data-ttu-id="c4dc9-118">不過，因為 HoloLens 2 的設計會增加相片/影片 (PV) 相機與顯示之間的距離，我們將會引進新的選項，來產生第 3 個相機轉譯對齊 PV 相機**HoloLens 2**。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-118">However, because the design of HoloLens 2 increases the distance between the photo/video (PV) camera and the display, we'll be introducing a new option to produce a 3rd camera render aligned to the PV camera of **HoloLens 2**.</span></span> 

<span data-ttu-id="c4dc9-119">選擇單元到第 3 個攝影機呈現 HoloLens 2 供應項目上下列增強功能對預設 MRC 經驗：</span><span class="sxs-lookup"><span data-stu-id="c4dc9-119">Opting-in to 3rd camera render on HoloLens 2 offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="c4dc9-120">全像您實體環境和實際操作 （適用於幾近互動） 的對齊方式應該是精確完全距離，而不是有的位移距離以外[專注點](focus-point-in-unity.md)您可能會看到預設 MRC 中。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-120">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the [focus point](focus-point-in-unity.md) as you might see in the default MRC.</span></span>
* <span data-ttu-id="c4dc9-121">耳機在右邊的眼睛將不會遭到入侵，因為它不會用來呈現全像投影 MRC 輸出。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-121">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="c4dc9-122">在您的應用程式中停用 MRC</span><span class="sxs-lookup"><span data-stu-id="c4dc9-122">Disabling MRC in your app</span></span>

<span data-ttu-id="c4dc9-123">當 2D 應用程式時，使用[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)或是[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)應用程式的視覺化內容將會顯示具有正確設定交換鏈結的受保護的內容，混合的實境擷取正在執行時，會自動隱藏。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-123">When a 2D app uses [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) or [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) to show protected content with a properly-configured swap chain, the app's visual content will be automatically obscured while mixed reality capture is running.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="c4dc9-124">了解當 MRC 在作用中</span><span class="sxs-lookup"><span data-stu-id="c4dc9-124">Knowing when MRC is active</span></span>

<span data-ttu-id="c4dc9-125">[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)類別可用的應用程式中了解混合實境擷取的系統 （例如音訊或視訊） 的執行時。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-125">The [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="c4dc9-126">AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API 可以傳回 null，如果混合實境擷取無法在裝置上使用。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-126">AppCapture's [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="c4dc9-127">務必也要取消註冊您的應用程式已暫止的 CapturingChanged 事件，否則 MRC 可以進入封鎖狀態。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-127">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="c4dc9-128">最佳作法 （特定的 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-128">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="c4dc9-129">MRC 應該可以運作而不需要額外的工作，從開發人員，但有幾件事要注意的以提供最適合混合的實境擷取經驗，您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-129">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="c4dc9-130">**MRC 使用全像圖的 alpha 色頻來與混合[相機](locatable-camera.md)圖像**</span><span class="sxs-lookup"><span data-stu-id="c4dc9-130">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="c4dc9-131">最重要的步驟是確定您的應用程式會藉由清除設為透明的黑色，而不是不透明的黑色的清除。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-131">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="c4dc9-132">在 Unity 中，這是藉由使用 MixedRealityToolkit 的預設值，但如果您正在開發非 Unity 中，您可能需要進行變更的一行。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-132">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="c4dc9-133">以下是一些您可能會看到在 MRC 如果您的應用程式不會清除為透明的黑色的成品：</span><span class="sxs-lookup"><span data-stu-id="c4dc9-133">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="c4dc9-134">**範例失敗**:（無法清除以透明的黑色） 內容周圍邊緣的黑色</span><span class="sxs-lookup"><span data-stu-id="c4dc9-134">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="c4dc9-135">**範例失敗**:整個背景場景的全像圖會顯示為黑色。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-135">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="c4dc9-136">黑色背景中設定背景 alpha 值的 1 個結果</span><span class="sxs-lookup"><span data-stu-id="c4dc9-136">Setting a background alpha value of 1 results in a black background</span></span>

![黑色背景中設定背景 alpha 值的 1 個結果](images/clearopaqueblack-300px.png)

<span data-ttu-id="c4dc9-138">**預期的結果**:全像投影出現正確混合使用真實世界 （如果設為透明黑色清除預期結果）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-138">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![預期的結果，如果設為透明黑色清除](images/cleartransparentblack-300px.png)

<span data-ttu-id="c4dc9-140">**解決方案**：</span><span class="sxs-lookup"><span data-stu-id="c4dc9-140">**Solution**:</span></span>
* <span data-ttu-id="c4dc9-141">變更為不透明的黑色出現有 alpha 值為 0 的任何內容。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-141">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="c4dc9-142">請確定應用程式會清除為透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-142">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="c4dc9-143">清除 自動清除 MixedRealityToolkit，但如果它是您應該修改與 ID3D11DeiceContext::ClearRenderTargetView() 搭配使用的色彩的非 Unity 應用程式使用的 unity 預設值。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-143">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="c4dc9-144">您想要確保您清除設為透明的黑色 (0,0,0,0)，而不是不透明的黑色 (0,0,0,1)。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-144">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="c4dc9-145">如果您想要但通常不需要您現在可以微調您的資產的 alpha 值。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-145">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="c4dc9-146">大部分的情況下，MRCs 看起來良好現成的。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-146">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="c4dc9-147">MRC 假設預乘的 alpha。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-147">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="c4dc9-148">Alpha 值只會影響 MRC 擷取。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-148">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="c4dc9-149">MRC HoloLens 上啟用時的行為</span><span class="sxs-lookup"><span data-stu-id="c4dc9-149">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="c4dc9-150">下列適用於 （第一代） 的 HoloLens 和 HoloLens 2，除非另有說明：</span><span class="sxs-lookup"><span data-stu-id="c4dc9-150">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="c4dc9-151">系統將會節流處理至 30 赫茲轉譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-151">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="c4dc9-152">這會建立執行，因此應用程式不需要保留固定的預算保留 MRC 一些成長空間，並也會比對的 30fps MRC 影片記錄畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="c4dc9-152">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="c4dc9-153">全像圖內容眼裡出正確的裝置時可能會出現以"火花"錄製/串流 MRC： 文字可能會變得更難以讀取和全像邊緣可能會出現更多鋸齒 (選擇單元到第 3 個攝影機上呈現**HoloLens 2**避免此入侵）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-153">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="c4dc9-154">MRC 相片和視訊，則會採用應用程式的[專注點](focus-point-in-unity.md)如果應用程式已啟用它，這將有助於確保全像投影會精確地放置。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-154">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="c4dc9-155">影片，焦點是經過平滑處理讓全像投影似乎緩慢漂移原位如果鶗懘深度發生重大變更。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-155">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="c4dc9-156">在不同的深度，焦點從全像投影中可能會顯示位移真實世界 （請參閱以下範例焦點設在 2 個計量，但闀位於 1 公尺）。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-156">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2 個計量在全像投影會完全註冊到世界。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="c4dc9-159">將從您的應用程式內的 MRC 功能整合</span><span class="sxs-lookup"><span data-stu-id="c4dc9-159">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="c4dc9-160">您的混合的實境應用程式可以起始 MRC 相片或視訊擷取在 app 中，和擷取的內容開放給您的應用程式而不儲存至裝置的 「 數位相機向前復原。 」</span><span class="sxs-lookup"><span data-stu-id="c4dc9-160">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="c4dc9-161">您可以建立自訂的 MRC 錄製器，或利用內建相機擷取 UI。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-161">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="c4dc9-162">使用內建相機 UI MRC</span><span class="sxs-lookup"><span data-stu-id="c4dc9-162">MRC with built-in camera UI</span></span>

<span data-ttu-id="c4dc9-163">開發人員可以使用*[相機擷取 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 取得的使用者擷取混合的實境相片或視訊，只要短短幾行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-163">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="c4dc9-164">此 API 會啟動內建 MRC 相機 UI，使用者可以拍攝相片或視訊，並傳回結果擷取到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-164">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="c4dc9-165">如果您想要建立您自己的相機 UI，或需要較低層級存取擷取資料流，您可以建立自訂的混合實境擷取錄製器。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-165">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="c4dc9-166">建立自訂的 MRC 錄製器</span><span class="sxs-lookup"><span data-stu-id="c4dc9-166">Creating a custom MRC recorder</span></span>

<span data-ttu-id="c4dc9-167">使用者一律可以觸發相片或視訊使用系統 MRC 擷取服務，而應用程式可能想要建置自訂的相機應用程式，但如同 MRC 相機資料流中包含全像投影中。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-167">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="c4dc9-168">這可讓應用程式開始執行代表使用者擷取、 建置自訂的錄製作業的 UI，或自訂 MRC 設定舉幾個例子。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-168">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="c4dc9-169">**HoloStudio 新增自訂 MRC 相機使用 MRC 效果**</span><span class="sxs-lookup"><span data-stu-id="c4dc9-169">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 新增自訂 MRC 相機使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="c4dc9-171">Unity 應用程式應該會看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)来啟用全像投影的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-171">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="c4dc9-172">其他應用程式可以使用來執行這[Windows 媒體擷取 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)控制相機，並新增 MRC 視訊和音訊效果中仍然可和影片包含虛擬全像投影和應用程式音訊。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-172">Other applications can do this by using the [Windows Media Capture APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="c4dc9-173">應用程式具有要新增效果的兩個選項：</span><span class="sxs-lookup"><span data-stu-id="c4dc9-173">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="c4dc9-174">較舊的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span><span class="sxs-lookup"><span data-stu-id="c4dc9-174">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span></span>
* <span data-ttu-id="c4dc9-175">新的 Microsoft 建議 API （傳回的物件，因此您能夠管理動態屬性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) ，您需要應用程式建立其自己實作[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)並[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-175">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) which require the app create its own implementation of [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) and [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx).</span></span> <span data-ttu-id="c4dc9-176">請參閱範例使用方式的 MRC 作用範例。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-176">Please see the MRC effect sample for sample usage.</span></span>

<span data-ttu-id="c4dc9-177">（請注意，Visual Studio 中，不會辨識這些命名空間，但字串仍然有效）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-177">(Note that these namespaces will not be recognized by Visual Studio, but the strings are still valid)</span></span>

<span data-ttu-id="c4dc9-178">MRC 視訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="c4dc9-178">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="c4dc9-179">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c4dc9-179">Property Name</span></span>  |  <span data-ttu-id="c4dc9-180">類型</span><span class="sxs-lookup"><span data-stu-id="c4dc9-180">Type</span></span>  |  <span data-ttu-id="c4dc9-181">預設值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-181">Default Value</span></span>  |  <span data-ttu-id="c4dc9-182">描述</span><span class="sxs-lookup"><span data-stu-id="c4dc9-182">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="c4dc9-183">StreamType</span><span class="sxs-lookup"><span data-stu-id="c4dc9-183">StreamType</span></span>  |  <span data-ttu-id="c4dc9-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span><span class="sxs-lookup"><span data-stu-id="c4dc9-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span></span>  |  <span data-ttu-id="c4dc9-185">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="c4dc9-185">1 (VideoRecord)</span></span>  |  <span data-ttu-id="c4dc9-186">描述對使用此效果的擷取資料流。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-186">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="c4dc9-187">不使用音訊。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-187">Audio is not available.</span></span> | 
|  <span data-ttu-id="c4dc9-188">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="c4dc9-188">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="c4dc9-189">布林值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-189">boolean</span></span>  |  <span data-ttu-id="c4dc9-190">TRUE</span><span class="sxs-lookup"><span data-stu-id="c4dc9-190">TRUE</span></span>  |  <span data-ttu-id="c4dc9-191">若要啟用或停用全像投影影片擷取畫面中的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-191">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="c4dc9-192">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="c4dc9-192">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="c4dc9-193">布林值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-193">boolean</span></span>  |  <span data-ttu-id="c4dc9-194">TRUE</span><span class="sxs-lookup"><span data-stu-id="c4dc9-194">TRUE</span></span>  |  <span data-ttu-id="c4dc9-195">若要啟用或停用在全像擷取的畫面上的記錄指標的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-195">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="c4dc9-196">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="c4dc9-196">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="c4dc9-197">布林值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-197">boolean</span></span>  |  <span data-ttu-id="c4dc9-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="c4dc9-198">FALSE</span></span>  |  <span data-ttu-id="c4dc9-199">若要啟用或停用由 HoloLens 追蹤器的視訊穩定功能旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-199">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="c4dc9-200">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="c4dc9-200">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="c4dc9-201">UINT32</span><span class="sxs-lookup"><span data-stu-id="c4dc9-201">UINT32</span></span>  |  <span data-ttu-id="c4dc9-202">0</span><span class="sxs-lookup"><span data-stu-id="c4dc9-202">0</span></span>  |  <span data-ttu-id="c4dc9-203">設定歷程記錄的框架數目用於視訊穩定功能。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-203">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="c4dc9-204">0 是 0 延遲和幾乎 「 免費 」 能力和效能的觀點。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-204">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="c4dc9-205">建議 （但要付出的延遲和記憶體的 15 框架） 的最高品質的 15。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-205">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="c4dc9-206">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="c4dc9-206">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="c4dc9-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="c4dc9-207">float</span></span>  |  <span data-ttu-id="c4dc9-208">0.9 (HoloLens) 1.0 （沈浸式耳機）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-208">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="c4dc9-209">設定全域的不透明度係數的全像範圍中從 0.0 （完全透明） 到 1.0 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-209">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="c4dc9-210">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="c4dc9-210">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="c4dc9-211">布林值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-211">boolean</span></span>  |  <span data-ttu-id="c4dc9-212">FALSE</span><span class="sxs-lookup"><span data-stu-id="c4dc9-212">FALSE</span></span>  |  <span data-ttu-id="c4dc9-213">若要啟用或停用 如果沒有 2d 的 UWP 應用程式顯示受保護的內容，傳回空框架的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-213">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="c4dc9-214">如果這個旗標設定為 false 且 2d UWP 應用程式會顯示受保護的內容、 2d 的 UWP 應用程式將會取代受保護的內容材質中這兩個耳機及混合的實境擷取畫面中。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-214">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="c4dc9-215">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="c4dc9-215">ShowHiddenMesh</span></span>  |  <span data-ttu-id="c4dc9-216">布林值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-216">boolean</span></span>  |  <span data-ttu-id="c4dc9-217">FALSE</span><span class="sxs-lookup"><span data-stu-id="c4dc9-217">FALSE</span></span>  |  <span data-ttu-id="c4dc9-218">若要啟用或停用顯示全像攝影版相機的隱藏的區域網格和相鄰內容的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-218">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |

<span data-ttu-id="c4dc9-219">MRC 音訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="c4dc9-219">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="c4dc9-220">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c4dc9-220">Property Name</span></span></th>
<th><span data-ttu-id="c4dc9-221">類型</span><span class="sxs-lookup"><span data-stu-id="c4dc9-221">Type</span></span></th>
<th><span data-ttu-id="c4dc9-222">預設值</span><span class="sxs-lookup"><span data-stu-id="c4dc9-222">Default Value</span></span></th>
<th><span data-ttu-id="c4dc9-223">描述</span><span class="sxs-lookup"><span data-stu-id="c4dc9-223">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="c4dc9-224">MixerMode</span><span class="sxs-lookup"><span data-stu-id="c4dc9-224">MixerMode</span></span></td>
<td><span data-ttu-id="c4dc9-225">UINT32</span><span class="sxs-lookup"><span data-stu-id="c4dc9-225">UINT32</span></span></td>
<td><span data-ttu-id="c4dc9-226">2</span><span class="sxs-lookup"><span data-stu-id="c4dc9-226">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="c4dc9-227">0 :僅限 mic 音訊</span><span class="sxs-lookup"><span data-stu-id="c4dc9-227">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="c4dc9-228">1 :僅限系統音訊</span><span class="sxs-lookup"><span data-stu-id="c4dc9-228">1 : System audio only</span></span></li>
<li><span data-ttu-id="c4dc9-229">2 :Mic 和系統音訊</span><span class="sxs-lookup"><span data-stu-id="c4dc9-229">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="c4dc9-230">同時 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="c4dc9-230">Simultaneous MRC limitations</span></span>

<span data-ttu-id="c4dc9-231">有多個應用程式在同一時間存取 MRC 周圍的某些限制。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-231">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="c4dc9-232">相片/影片相機存取</span><span class="sxs-lookup"><span data-stu-id="c4dc9-232">Photo/video camera access</span></span>

<span data-ttu-id="c4dc9-233">相片或視訊攝影機僅限於在同一時間可以存取它的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-233">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="c4dc9-234">處理序正在錄製影片，或利用任何其他處理序的相片將會失敗取得相片/影片相機。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-234">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="c4dc9-235">（這適用於混合實境擷取和標準的相片/影片擷取）</span><span class="sxs-lookup"><span data-stu-id="c4dc9-235">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="c4dc9-236">使用 Windows 10 April 2018 Update，這項限制不適用於如果內建的 MRC 相機 UI 用來讓照相或拍攝影片之後應用程式已開始使用相片/影片相機。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-236">With the Windows 10 April 2018 Update, this restriction does not apply if the built-in MRC camera UI is used to take a photo or a video after an app has started using the photo/video camera.</span></span> <span data-ttu-id="c4dc9-237">當發生這種情況的內建的 MRC 相機 UI 畫面播放速率與解析度可能會降低其一般的值。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-237">When this happens, the resolution and framerate of the built-in MRC camera UI might be reduced from its normal values.</span></span>

<span data-ttu-id="c4dc9-238">使用 Windows 10 年 10 月 2018 Update，這項限制不適用於透過 Miracast 串流 MRC。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-238">With the Windows 10 October 2018 Update, this restriction does not apply to streaming MRC over Miracast.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="c4dc9-239">MRC 存取</span><span class="sxs-lookup"><span data-stu-id="c4dc9-239">MRC access</span></span>

<span data-ttu-id="c4dc9-240">使用 Windows 10 April 2018 Update，不再有多個應用程式存取 （不過，存取相片/影片相機仍有限制） MRC 資料流周圍的限制。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-240">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="c4dc9-241">先前的 windows 10 April 2018 Update，應用程式的自訂 MRC 錄製器已與系統 MRC （擷取相片、 擷取影片或來自 Windows Device Portal） 互斥。</span><span class="sxs-lookup"><span data-stu-id="c4dc9-241">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4dc9-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4dc9-242">See also</span></span>
* [<span data-ttu-id="c4dc9-243">混合的實境擷取</span><span class="sxs-lookup"><span data-stu-id="c4dc9-243">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="c4dc9-244">Spectator 檢視</span><span class="sxs-lookup"><span data-stu-id="c4dc9-244">Spectator view</span></span>](spectator-view.md)
