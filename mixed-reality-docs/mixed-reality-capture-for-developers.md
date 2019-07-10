---
title: 混合實境擷取適用於開發人員
description: 適用於開發人員，擷取的混合實境的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 相片、 視訊、 擷取、 相機
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694367"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="9793b-104">混合實境擷取適用於開發人員</span><span class="sxs-lookup"><span data-stu-id="9793b-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="9793b-105">[注意 ！]請參閱[PV 相機中呈現](#render-from-the-pv-camera-opt-in)以下新的 MRC 功能有關的 HoloLens 2 指導方針。</span><span class="sxs-lookup"><span data-stu-id="9793b-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="9793b-106">因為使用者無法接管[混合實境擷取](mixed-reality-capture.md)(MRC) 相片或視訊在任何時間，有幾件事開發您的應用程式時，您應該謹記在心。</span><span class="sxs-lookup"><span data-stu-id="9793b-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="9793b-107">這包括 MRC 視覺品質和正在回應系統的變更，正在擷取 MRCs 時的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="9793b-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="9793b-108">開發人員可以也會順暢地整合混合的實境擷取和插入自己的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9793b-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="9793b-109">MRC HoloLens （第一代） 上的支援視訊和相片最多 720p，雖然 MRC HoloLens 2 上的啟動支援高達 1080p 和相片的影片，4k 解析度。</span><span class="sxs-lookup"><span data-stu-id="9793b-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="9793b-110">品質 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="9793b-110">The importance of quality MRC</span></span>

<span data-ttu-id="9793b-111">混合的實境擷取相片和影片可能是使用者會有您的應用程式的第一次。</span><span class="sxs-lookup"><span data-stu-id="9793b-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="9793b-112">是否為您的 Microsoft Store 頁面上，或從共用 MRCs 社交網路上其他使用者的混合的實境螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="9793b-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="9793b-113">您可以使用 MRC 來示範您的應用程式，所以請教導使用者，鼓勵使用者共用其混合的環境的互動，以及根據使用者研究和解決問題。</span><span class="sxs-lookup"><span data-stu-id="9793b-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="9793b-114">MRC 會如何影響您的應用程式</span><span class="sxs-lookup"><span data-stu-id="9793b-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="9793b-115">應用程式中啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="9793b-115">Enabling MRC in your app</span></span>

<span data-ttu-id="9793b-116">根據預設，應用程式並沒有採取任何動作，讓使用者可以採取混合的實境擷取。</span><span class="sxs-lookup"><span data-stu-id="9793b-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="9793b-117">啟用 MRC 應用程式中的改善的調整</span><span class="sxs-lookup"><span data-stu-id="9793b-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="9793b-118">根據預設，混合的實境擷取會結合相片/影片 (PV) 相機右邊的眼睛全像攝影版的輸出。</span><span class="sxs-lookup"><span data-stu-id="9793b-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="9793b-119">這些兩個來源會結合使用由目前執行的沈浸式應用程式設定的焦點。</span><span class="sxs-lookup"><span data-stu-id="9793b-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="9793b-120">這表示全像投影焦點平面之外，不會對齊也 （因為 PV 觀景窗之間的正確顯示實際的距離）。</span><span class="sxs-lookup"><span data-stu-id="9793b-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="9793b-121">設定焦點</span><span class="sxs-lookup"><span data-stu-id="9793b-121">Set the focus point</span></span>

<span data-ttu-id="9793b-122">（在 HoloLens) 的沈浸式應用程式應該設定[專注點](focus-point-in-unity.md)使用者想要其穩定平面的位置。</span><span class="sxs-lookup"><span data-stu-id="9793b-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="9793b-123">這可確保最佳的對齊方式，在這兩個耳機和混合的實境擷取。</span><span class="sxs-lookup"><span data-stu-id="9793b-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="9793b-124">如果未設定婧鎏鶗懘，穩定平面將會預設為兩個計量。</span><span class="sxs-lookup"><span data-stu-id="9793b-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="9793b-125">呈現從 PV 相機 （選用功能）</span><span class="sxs-lookup"><span data-stu-id="9793b-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="9793b-126">HoloLens 2 加入沈浸式應用程式的能力**PV 相機中呈現**混合的實境擷取正在執行時。</span><span class="sxs-lookup"><span data-stu-id="9793b-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="9793b-127">若要確保正確的應用程式支援的其他轉譯，則應用程式必須 opt-in 以這項功能。</span><span class="sxs-lookup"><span data-stu-id="9793b-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="9793b-128">轉譯 PV 相機的供應項目從以下的改良，對預設 MRC 經驗：</span><span class="sxs-lookup"><span data-stu-id="9793b-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="9793b-129">全像您實體環境和實際操作 （適用於幾近互動） 的對齊方式應該是正確的完全距離，而不需要在焦點點以外的距離的位移，您可能會看到預設 MRC。</span><span class="sxs-lookup"><span data-stu-id="9793b-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="9793b-130">耳機在右邊的眼睛將不會遭到入侵，因為它不會用來呈現全像投影 MRC 輸出。</span><span class="sxs-lookup"><span data-stu-id="9793b-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="9793b-131">有三個步驟，若要啟用轉譯從 PV 相機：</span><span class="sxs-lookup"><span data-stu-id="9793b-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="9793b-132">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="9793b-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="9793b-133">處理其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="9793b-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="9793b-134">請確認您的著色器和程式碼正確呈現此額外 HolographicCamera 從</span><span class="sxs-lookup"><span data-stu-id="9793b-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="9793b-135">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="9793b-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="9793b-136">若要選擇加入應用程式只是讓 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="9793b-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="9793b-137">處理其他 HolographicCamera 呈現在 DirectX</span><span class="sxs-lookup"><span data-stu-id="9793b-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="9793b-138">當應用程式已選擇加入要呈現從 PV 相機及混合的實境擷取功能開始：</span><span class="sxs-lookup"><span data-stu-id="9793b-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="9793b-139">HolographicSpace 的 CameraAdded 事件就會引發。</span><span class="sxs-lookup"><span data-stu-id="9793b-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="9793b-140">如果應用程式無法處理觀景窗在這個階段，就會延期此事件。</span><span class="sxs-lookup"><span data-stu-id="9793b-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="9793b-141">當事件完成 （而且有任何未完成延期時） HolographicCamera 會出現在下一步 的 HolographicFrame AddedCameras 清單中。</span><span class="sxs-lookup"><span data-stu-id="9793b-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="9793b-142">當混合的實境擷取停駐點 （或應用程式在混合的實境擷取正在執行時，會停用檢視設定）： HolographicCamera 會出現在下一步 的 HolographicFrame RemovedCameras 清單和 HolographicSpace CameraRemoved 事件將引發。</span><span class="sxs-lookup"><span data-stu-id="9793b-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="9793b-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) HolographicCamera 以協助找出相機所屬的設定已加入屬性。</span><span class="sxs-lookup"><span data-stu-id="9793b-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="9793b-144">處理其他 HolographicCamera 呈現在 Unity 中</span><span class="sxs-lookup"><span data-stu-id="9793b-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="9793b-145">要呈現 PV 相機中的 unity 支援正在開發，尚無法使用。</span><span class="sxs-lookup"><span data-stu-id="9793b-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="9793b-146">PV 相機中的轉譯支援 Unity 組建可用時，將會更新這份文件。</span><span class="sxs-lookup"><span data-stu-id="9793b-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="9793b-147">確認著色器和程式碼支援其他觀景窗</span><span class="sxs-lookup"><span data-stu-id="9793b-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="9793b-148">執行混合的實境擷取和檢查有不尋常的對齊方式、 遺失的內容或效能問題。</span><span class="sxs-lookup"><span data-stu-id="9793b-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="9793b-149">更新著色器和適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9793b-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="9793b-150">某些無法支援額外的攝影機呈現的場景時，您可以在這些期間停用 PhotoVideoCamera HolographicViewConfiguration。</span><span class="sxs-lookup"><span data-stu-id="9793b-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="9793b-151">在您的應用程式中停用 MRC</span><span class="sxs-lookup"><span data-stu-id="9793b-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="9793b-152">2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="9793b-152">2D app</span></span>

<span data-ttu-id="9793b-153">2D 應用程式可以選擇隱藏執行混合的實境擷取時其視覺化內容：</span><span class="sxs-lookup"><span data-stu-id="9793b-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="9793b-154">看見[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)旗標</span><span class="sxs-lookup"><span data-stu-id="9793b-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="9793b-155">建立具有應用程式的交換鏈結[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)旗標</span><span class="sxs-lookup"><span data-stu-id="9793b-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="9793b-156">Windows 10 可能 2019年更新，請設定 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="9793b-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="9793b-157">沈浸式應用程式</span><span class="sxs-lookup"><span data-stu-id="9793b-157">Immersive app</span></span>

<span data-ttu-id="9793b-158">沈浸式應用程式可以選擇排除，藉以混合的實境擷取其視覺化內容：</span><span class="sxs-lookup"><span data-stu-id="9793b-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="9793b-159">設定的 HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)停用混合的實境擷取其相關聯的框架</span><span class="sxs-lookup"><span data-stu-id="9793b-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="9793b-160">設定的 HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)停用其相關聯的全像攝影版相機的混合的實境擷取</span><span class="sxs-lookup"><span data-stu-id="9793b-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="9793b-161">密碼鍵盤</span><span class="sxs-lookup"><span data-stu-id="9793b-161">Password Keyboard</span></span>

<span data-ttu-id="9793b-162">Windows 10 可能 2019年的更新，可以看到密碼或 pin 碼的鍵盤時，混合的實境擷取自動排除視覺內容。</span><span class="sxs-lookup"><span data-stu-id="9793b-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="9793b-163">了解當 MRC 在作用中</span><span class="sxs-lookup"><span data-stu-id="9793b-163">Knowing when MRC is active</span></span>

<span data-ttu-id="9793b-164">[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別可用的應用程式中了解混合實境擷取的系統 （例如音訊或視訊） 的執行時。</span><span class="sxs-lookup"><span data-stu-id="9793b-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="9793b-165">AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以傳回 null，如果混合實境擷取無法在裝置上使用。</span><span class="sxs-lookup"><span data-stu-id="9793b-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="9793b-166">務必也要取消註冊您的應用程式已暫止的 CapturingChanged 事件，否則 MRC 可以進入封鎖狀態。</span><span class="sxs-lookup"><span data-stu-id="9793b-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="9793b-167">最佳作法 （特定的 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="9793b-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="9793b-168">MRC 應該可以運作而不需要額外的工作，從開發人員，但有幾件事要注意的以提供最適合混合的實境擷取經驗，您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9793b-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="9793b-169">**MRC 使用全像圖的 alpha 色頻來與混合[相機](locatable-camera.md)圖像**</span><span class="sxs-lookup"><span data-stu-id="9793b-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="9793b-170">最重要的步驟是確定您的應用程式會藉由清除設為透明的黑色，而不是不透明的黑色的清除。</span><span class="sxs-lookup"><span data-stu-id="9793b-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="9793b-171">在 Unity 中，這是藉由使用 MixedRealityToolkit 的預設值，但如果您正在開發非 Unity 中，您可能需要進行變更的一行。</span><span class="sxs-lookup"><span data-stu-id="9793b-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="9793b-172">以下是一些您可能會看到在 MRC 如果您的應用程式不會清除為透明的黑色的成品：</span><span class="sxs-lookup"><span data-stu-id="9793b-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="9793b-173">**範例失敗**:（無法清除以透明的黑色） 內容周圍邊緣的黑色</span><span class="sxs-lookup"><span data-stu-id="9793b-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="9793b-174">**範例失敗**:整個背景場景的全像圖會顯示為黑色。</span><span class="sxs-lookup"><span data-stu-id="9793b-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="9793b-175">黑色背景中設定背景 alpha 值的 1 個結果</span><span class="sxs-lookup"><span data-stu-id="9793b-175">Setting a background alpha value of 1 results in a black background</span></span>

![黑色背景中設定背景 alpha 值的 1 個結果](images/clearopaqueblack-300px.png)

<span data-ttu-id="9793b-177">**預期的結果**:全像投影出現正確混合使用真實世界 （如果設為透明黑色清除預期結果）</span><span class="sxs-lookup"><span data-stu-id="9793b-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![預期的結果，如果設為透明黑色清除](images/cleartransparentblack-300px.png)

<span data-ttu-id="9793b-179">**解決方案**：</span><span class="sxs-lookup"><span data-stu-id="9793b-179">**Solution**:</span></span>
* <span data-ttu-id="9793b-180">變更為不透明的黑色出現有 alpha 值為 0 的任何內容。</span><span class="sxs-lookup"><span data-stu-id="9793b-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="9793b-181">請確定應用程式會清除為透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="9793b-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="9793b-182">清除 自動清除 MixedRealityToolkit，但如果它是您應該修改與 ID3D11DeiceContext::ClearRenderTargetView() 搭配使用的色彩的非 Unity 應用程式使用的 unity 預設值。</span><span class="sxs-lookup"><span data-stu-id="9793b-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="9793b-183">您想要確保您清除設為透明的黑色 (0,0,0,0)，而不是不透明的黑色 (0,0,0,1)。</span><span class="sxs-lookup"><span data-stu-id="9793b-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="9793b-184">如果您想要但通常不需要您現在可以微調您的資產的 alpha 值。</span><span class="sxs-lookup"><span data-stu-id="9793b-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="9793b-185">大部分的情況下，MRCs 看起來良好現成的。</span><span class="sxs-lookup"><span data-stu-id="9793b-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="9793b-186">MRC 假設預乘的 alpha。</span><span class="sxs-lookup"><span data-stu-id="9793b-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="9793b-187">Alpha 值只會影響 MRC 擷取。</span><span class="sxs-lookup"><span data-stu-id="9793b-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="9793b-188">MRC HoloLens 上啟用時的行為</span><span class="sxs-lookup"><span data-stu-id="9793b-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="9793b-189">下列適用於 （第一代） 的 HoloLens 和 HoloLens 2，除非另有說明：</span><span class="sxs-lookup"><span data-stu-id="9793b-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="9793b-190">系統將會節流處理至 30 赫茲轉譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="9793b-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="9793b-191">這會建立執行，因此應用程式不需要保留固定的預算保留 MRC 一些成長空間，並也會比對的 30fps MRC 影片記錄畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="9793b-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="9793b-192">全像圖內容眼裡出正確的裝置時可能會出現以"火花"錄製/串流 MRC： 文字可能會變得更難以讀取和全像邊緣可能會出現更多鋸齒 (選擇單元到第 3 個攝影機上呈現**HoloLens 2**避免此入侵）</span><span class="sxs-lookup"><span data-stu-id="9793b-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="9793b-193">MRC 相片和視訊，則會採用應用程式的[專注點](focus-point-in-unity.md)如果應用程式已啟用它，這將有助於確保全像投影會精確地放置。</span><span class="sxs-lookup"><span data-stu-id="9793b-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="9793b-194">影片，焦點是經過平滑處理讓全像投影似乎緩慢漂移原位如果鶗懘深度發生重大變更。</span><span class="sxs-lookup"><span data-stu-id="9793b-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="9793b-195">在不同的深度，焦點從全像投影中可能會顯示位移真實世界 （請參閱以下範例焦點設在 2 個計量，但闀位於 1 公尺）。</span><span class="sxs-lookup"><span data-stu-id="9793b-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2 個計量在全像投影會完全註冊到世界。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="9793b-198">將從您的應用程式內的 MRC 功能整合</span><span class="sxs-lookup"><span data-stu-id="9793b-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="9793b-199">您的混合的實境應用程式可以起始 MRC 相片或視訊擷取在 app 中，和擷取的內容開放給您的應用程式而不儲存至裝置的 「 數位相機向前復原。 」</span><span class="sxs-lookup"><span data-stu-id="9793b-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="9793b-200">您可以建立自訂的 MRC 錄製器，或利用內建相機擷取 UI。</span><span class="sxs-lookup"><span data-stu-id="9793b-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="9793b-201">使用內建相機 UI MRC</span><span class="sxs-lookup"><span data-stu-id="9793b-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="9793b-202">開發人員可以使用 *[相機擷取 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 取得的使用者擷取混合的實境相片或視訊，只要短短幾行程式碼。</span><span class="sxs-lookup"><span data-stu-id="9793b-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="9793b-203">此 API 會啟動內建 MRC 相機 UI，使用者可以拍攝相片或視訊，並傳回結果擷取到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9793b-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="9793b-204">如果您想要建立您自己的相機 UI，或需要較低層級存取擷取資料流，您可以建立自訂的混合實境擷取錄製器。</span><span class="sxs-lookup"><span data-stu-id="9793b-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="9793b-205">建立自訂的 MRC 錄製器</span><span class="sxs-lookup"><span data-stu-id="9793b-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="9793b-206">使用者一律可以觸發相片或視訊使用系統 MRC 擷取服務，而應用程式可能想要建置自訂的相機應用程式，但如同 MRC 相機資料流中包含全像投影中。</span><span class="sxs-lookup"><span data-stu-id="9793b-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="9793b-207">這可讓應用程式開始執行代表使用者擷取、 建置自訂的錄製作業的 UI，或自訂 MRC 設定舉幾個例子。</span><span class="sxs-lookup"><span data-stu-id="9793b-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="9793b-208">**HoloStudio 新增自訂 MRC 相機使用 MRC 效果**</span><span class="sxs-lookup"><span data-stu-id="9793b-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 新增自訂 MRC 相機使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="9793b-210">Unity 應用程式應該會看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)来啟用全像投影的屬性。</span><span class="sxs-lookup"><span data-stu-id="9793b-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="9793b-211">其他應用程式可以使用來執行這[Windows 媒體擷取 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相機，並新增 MRC 視訊和音訊效果中仍然可和影片包含虛擬全像投影和應用程式音訊。</span><span class="sxs-lookup"><span data-stu-id="9793b-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="9793b-212">應用程式具有要新增效果的兩個選項：</span><span class="sxs-lookup"><span data-stu-id="9793b-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="9793b-213">較舊的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="9793b-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="9793b-214">新的 Microsoft 建議 API （傳回的物件，因此您能夠管理動態屬性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，您需要應用程式建立其自己實作[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)並[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。</span><span class="sxs-lookup"><span data-stu-id="9793b-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="9793b-215">請參閱範例使用方式的 MRC 作用範例。</span><span class="sxs-lookup"><span data-stu-id="9793b-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="9793b-216">Visual Studio 中，不會辨識 Windows.Media.MixedRealityCapture 命名空間，但字串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="9793b-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="9793b-217">MRC 視訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="9793b-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="9793b-218">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="9793b-218">Property Name</span></span>  |  <span data-ttu-id="9793b-219">type</span><span class="sxs-lookup"><span data-stu-id="9793b-219">Type</span></span>  |  <span data-ttu-id="9793b-220">Default Value</span><span class="sxs-lookup"><span data-stu-id="9793b-220">Default Value</span></span>  |  <span data-ttu-id="9793b-221">描述</span><span class="sxs-lookup"><span data-stu-id="9793b-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="9793b-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="9793b-222">StreamType</span></span>  |  <span data-ttu-id="9793b-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="9793b-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="9793b-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="9793b-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="9793b-225">描述對使用此效果的擷取資料流。</span><span class="sxs-lookup"><span data-stu-id="9793b-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="9793b-226">不使用音訊。</span><span class="sxs-lookup"><span data-stu-id="9793b-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="9793b-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="9793b-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="9793b-228">boolean</span><span class="sxs-lookup"><span data-stu-id="9793b-228">boolean</span></span>  |  <span data-ttu-id="9793b-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="9793b-229">TRUE</span></span>  |  <span data-ttu-id="9793b-230">若要啟用或停用全像投影影片擷取畫面中的旗標。</span><span class="sxs-lookup"><span data-stu-id="9793b-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="9793b-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="9793b-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="9793b-232">boolean</span><span class="sxs-lookup"><span data-stu-id="9793b-232">boolean</span></span>  |  <span data-ttu-id="9793b-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="9793b-233">TRUE</span></span>  |  <span data-ttu-id="9793b-234">若要啟用或停用在全像擷取的畫面上的記錄指標的旗標。</span><span class="sxs-lookup"><span data-stu-id="9793b-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="9793b-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="9793b-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="9793b-236">boolean</span><span class="sxs-lookup"><span data-stu-id="9793b-236">boolean</span></span>  |  <span data-ttu-id="9793b-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="9793b-237">FALSE</span></span>  |  <span data-ttu-id="9793b-238">若要啟用或停用由 HoloLens 追蹤器的視訊穩定功能旗標。</span><span class="sxs-lookup"><span data-stu-id="9793b-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="9793b-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="9793b-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="9793b-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="9793b-240">UINT32</span></span>  |  <span data-ttu-id="9793b-241">0</span><span class="sxs-lookup"><span data-stu-id="9793b-241">0</span></span>  |  <span data-ttu-id="9793b-242">設定歷程記錄的框架數目用於視訊穩定功能。</span><span class="sxs-lookup"><span data-stu-id="9793b-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="9793b-243">0 是 0 延遲和幾乎 「 免費 」 能力和效能的觀點。</span><span class="sxs-lookup"><span data-stu-id="9793b-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="9793b-244">建議 （但要付出的延遲和記憶體的 15 框架） 的最高品質的 15。</span><span class="sxs-lookup"><span data-stu-id="9793b-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="9793b-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="9793b-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="9793b-246">FLOAT</span><span class="sxs-lookup"><span data-stu-id="9793b-246">float</span></span>  |  <span data-ttu-id="9793b-247">0.9 (HoloLens) 1.0 （沈浸式耳機）</span><span class="sxs-lookup"><span data-stu-id="9793b-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="9793b-248">設定全域的不透明度係數的全像範圍中從 0.0 （完全透明） 到 1.0 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="9793b-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="9793b-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="9793b-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="9793b-250">boolean</span><span class="sxs-lookup"><span data-stu-id="9793b-250">boolean</span></span>  |  <span data-ttu-id="9793b-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="9793b-251">FALSE</span></span>  |  <span data-ttu-id="9793b-252">若要啟用或停用 如果沒有 2d 的 UWP 應用程式顯示受保護的內容，傳回空框架的旗標。</span><span class="sxs-lookup"><span data-stu-id="9793b-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="9793b-253">如果這個旗標設定為 false 且 2d UWP 應用程式會顯示受保護的內容、 2d 的 UWP 應用程式將會取代受保護的內容材質中這兩個耳機及混合的實境擷取畫面中。</span><span class="sxs-lookup"><span data-stu-id="9793b-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="9793b-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="9793b-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="9793b-255">boolean</span><span class="sxs-lookup"><span data-stu-id="9793b-255">boolean</span></span>  |  <span data-ttu-id="9793b-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="9793b-256">FALSE</span></span>  |  <span data-ttu-id="9793b-257">若要啟用或停用顯示全像攝影版相機的隱藏的區域網格和相鄰內容的旗標。</span><span class="sxs-lookup"><span data-stu-id="9793b-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="9793b-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="9793b-258">OutputSize</span></span> | <span data-ttu-id="9793b-259">Size</span><span class="sxs-lookup"><span data-stu-id="9793b-259">Size</span></span> | <span data-ttu-id="9793b-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="9793b-260">0, 0</span></span> | <span data-ttu-id="9793b-261">在剪輯的視訊穩定後，設定想要的輸出大小。</span><span class="sxs-lookup"><span data-stu-id="9793b-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="9793b-262">如果指定了 0 或無效的輸出大小，則會選擇預設裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="9793b-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="9793b-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="9793b-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="9793b-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="9793b-264">UINT32</span></span> | <span data-ttu-id="9793b-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="9793b-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="9793b-266">列舉用來指出應該擷取哪種全像攝影版的相機檢視設定。</span><span class="sxs-lookup"><span data-stu-id="9793b-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="9793b-267">設定 0 （顯示器） 表示應用程式不會呈現從相片或視訊攝影機要求</span><span class="sxs-lookup"><span data-stu-id="9793b-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="9793b-268">MRC 音訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="9793b-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="9793b-269">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="9793b-269">Property Name</span></span></th>
<th><span data-ttu-id="9793b-270">type</span><span class="sxs-lookup"><span data-stu-id="9793b-270">Type</span></span></th>
<th><span data-ttu-id="9793b-271">Default Value</span><span class="sxs-lookup"><span data-stu-id="9793b-271">Default Value</span></span></th>
<th><span data-ttu-id="9793b-272">描述</span><span class="sxs-lookup"><span data-stu-id="9793b-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="9793b-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="9793b-273">MixerMode</span></span></td>
<td><span data-ttu-id="9793b-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="9793b-274">UINT32</span></span></td>
<td><span data-ttu-id="9793b-275">2</span><span class="sxs-lookup"><span data-stu-id="9793b-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="9793b-276">0 :僅限 mic 音訊</span><span class="sxs-lookup"><span data-stu-id="9793b-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="9793b-277">1 :僅限系統音訊</span><span class="sxs-lookup"><span data-stu-id="9793b-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="9793b-278">2 :Mic 和系統音訊</span><span class="sxs-lookup"><span data-stu-id="9793b-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="9793b-279">同時 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="9793b-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="9793b-280">有多個應用程式在同一時間存取 MRC 周圍的某些限制。</span><span class="sxs-lookup"><span data-stu-id="9793b-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="9793b-281">相片/影片相機存取</span><span class="sxs-lookup"><span data-stu-id="9793b-281">Photo/video camera access</span></span>

<span data-ttu-id="9793b-282">相片或視訊攝影機僅限於在同一時間可以存取它的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="9793b-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="9793b-283">處理序正在錄製影片，或利用任何其他處理序的相片將會失敗取得相片/影片相機。</span><span class="sxs-lookup"><span data-stu-id="9793b-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="9793b-284">（這適用於混合實境擷取和標準的相片/影片擷取）</span><span class="sxs-lookup"><span data-stu-id="9793b-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="9793b-285">HoloLens 2 應用程式可以使用的 MediaCaptureInitializationSettings [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)屬性，指出他們想要執行 SharedReadOnly，如果它們不需要將相片/攝影機的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="9793b-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="9793b-286">擷取的畫面播放速率與解析度，這樣做表示會受限於其他應用程式已設定的項目提供的相機。</span><span class="sxs-lookup"><span data-stu-id="9793b-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="9793b-287">內建 MRC 相片/影片相機存取</span><span class="sxs-lookup"><span data-stu-id="9793b-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="9793b-288">內建於 Windows 10 （透過 Cortana、 [開始] 功能表、 硬體快速鍵 Miracast、 Windows Device Portal） MRC 功能：</span><span class="sxs-lookup"><span data-stu-id="9793b-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="9793b-289">預設會使用 ExclusiveControl 執行</span><span class="sxs-lookup"><span data-stu-id="9793b-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="9793b-290">不過，支援已新增至每個子系統，在共用模式中運作：</span><span class="sxs-lookup"><span data-stu-id="9793b-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="9793b-291">如果應用程式要求 ExclusiveControl 存取相片/攝影機，內建 MRC 將會自動停止使用相片/攝影機，因此應用程式的要求將會成功</span><span class="sxs-lookup"><span data-stu-id="9793b-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="9793b-292">如果內建 MRC 已啟動時，應用程式必須 ExclusiveControl，內建 MRC 將以 SharedReadOnly 模式執行</span><span class="sxs-lookup"><span data-stu-id="9793b-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="9793b-293">此共用的模式功能具有某些限制：</span><span class="sxs-lookup"><span data-stu-id="9793b-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="9793b-294">相片透過 Cortana、 硬體的捷徑或 [開始] 功能表：需要 Windows 10 April 2018 Update （或更新版本）</span><span class="sxs-lookup"><span data-stu-id="9793b-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="9793b-295">透過 Cortana、 硬體的捷徑或 [開始] 功能表的影片：需要 Windows 10 April 2018 Update （或更新版本）</span><span class="sxs-lookup"><span data-stu-id="9793b-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="9793b-296">資料流透過 Miracast MRC:需要 Windows 10 年 10 月 2018年更新 （或更新版本）</span><span class="sxs-lookup"><span data-stu-id="9793b-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="9793b-297">透過 Windows Device Portal，或透過 HoloLens 小幫手應用程式的資料流 MRC:需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9793b-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="9793b-298">內建的 MRC 相機 UI 畫面播放速率與解析度可能會降低其一般的值從另一個應用程式使用相片/攝影機時。</span><span class="sxs-lookup"><span data-stu-id="9793b-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="9793b-299">MRC 存取</span><span class="sxs-lookup"><span data-stu-id="9793b-299">MRC access</span></span>

<span data-ttu-id="9793b-300">使用 Windows 10 April 2018 Update，不再有多個應用程式存取 （不過，存取相片/影片相機仍有限制） MRC 資料流周圍的限制。</span><span class="sxs-lookup"><span data-stu-id="9793b-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="9793b-301">先前的 windows 10 April 2018 Update，應用程式的自訂 MRC 錄製器已與系統 MRC （擷取相片、 擷取影片或來自 Windows Device Portal） 互斥。</span><span class="sxs-lookup"><span data-stu-id="9793b-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="9793b-302">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9793b-302">See also</span></span>
* [<span data-ttu-id="9793b-303">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="9793b-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="9793b-304">觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="9793b-304">Spectator view</span></span>](spectator-view.md)
