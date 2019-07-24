---
title: 開發人員的混合現實 capture
description: 開發人員混合現實的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、相片、影片、capture、攝影機
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694367"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="024c8-104">開發人員的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="024c8-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="024c8-105">[注意!]如需 HoloLens 2 新 MRC 功能的指引, 請參閱下列[PV 攝影機](#render-from-the-pv-camera-opt-in)的轉譯。</span><span class="sxs-lookup"><span data-stu-id="024c8-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="024c8-106">由於使用者可以隨時採取[混合現實 capture](mixed-reality-capture.md) (MRC) 相片或影片, 因此在開發應用程式時, 您應該記住幾件事。</span><span class="sxs-lookup"><span data-stu-id="024c8-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="024c8-107">這包括 MRC 視覺品質的最佳做法, 並在 MRCs 時回應系統變更。</span><span class="sxs-lookup"><span data-stu-id="024c8-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="024c8-108">開發人員也可以順暢地將混合現實的 capture 和插入整合到其應用程式中。</span><span class="sxs-lookup"><span data-stu-id="024c8-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="024c8-109">HoloLens (第一代) 上的 MRC 支援最多720p 的影片和相片, 而 HoloLens 2 上的 MRC 則支援最高1080p 和最多4K 解析度的影像。</span><span class="sxs-lookup"><span data-stu-id="024c8-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="024c8-110">品質 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="024c8-110">The importance of quality MRC</span></span>

<span data-ttu-id="024c8-111">混合現實已捕捉的相片和影片可能是使用者在您的應用程式中的第一次曝光。</span><span class="sxs-lookup"><span data-stu-id="024c8-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="024c8-112">在您的 Microsoft Store 頁面上, 還是在社交網路上共用 MRCs 的其他使用者上, 是否為混合現實螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="024c8-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="024c8-113">您可以使用 MRC 來示範您的應用程式、教育使用者、鼓勵使用者分享其混合世界互動, 以及進行使用者研究和問題解決。</span><span class="sxs-lookup"><span data-stu-id="024c8-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="024c8-114">MRC 如何影響您的應用程式</span><span class="sxs-lookup"><span data-stu-id="024c8-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="024c8-115">在您的應用程式中啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="024c8-115">Enabling MRC in your app</span></span>

<span data-ttu-id="024c8-116">根據預設, 應用程式不需要執行任何動作, 即可讓使用者進行混合的事實捕捉。</span><span class="sxs-lookup"><span data-stu-id="024c8-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="024c8-117">針對您應用程式中的 MRC 啟用改良的對齊</span><span class="sxs-lookup"><span data-stu-id="024c8-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="024c8-118">根據預設, 混合現實 capture 會將適當的全像攝影輸出與相片/影片 (PV) 攝影機結合。</span><span class="sxs-lookup"><span data-stu-id="024c8-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="024c8-119">這兩個來源會使用目前執行的沉浸式應用程式所設定的焦點點進行結合。</span><span class="sxs-lookup"><span data-stu-id="024c8-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="024c8-120">這表示焦點平面外的全息影像也不會對齊 (因為 PV 攝影機和右邊顯示之間的實體距離)。</span><span class="sxs-lookup"><span data-stu-id="024c8-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="024c8-121">設定焦點點</span><span class="sxs-lookup"><span data-stu-id="024c8-121">Set the focus point</span></span>

<span data-ttu-id="024c8-122">沉浸式應用程式 (在 HoloLens 上) 應該設定其穩定平面所在的[焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="024c8-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="024c8-123">這可確保耳機和混合現實 capture 中的最佳對齊方式。</span><span class="sxs-lookup"><span data-stu-id="024c8-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="024c8-124">如果未設定焦點, 穩定平面會預設為兩個計量。</span><span class="sxs-lookup"><span data-stu-id="024c8-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="024c8-125">從 PV 攝影機轉譯 (加入宣告)</span><span class="sxs-lookup"><span data-stu-id="024c8-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="024c8-126">HoloLens 2 增加了當混合現實捕捉正在執行時, 沉浸式應用程式**從 PV 攝影機**轉譯的功能。</span><span class="sxs-lookup"><span data-stu-id="024c8-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="024c8-127">為了確保應用程式能夠正確支援額外的轉譯, 應用程式必須加入宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="024c8-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="024c8-128">從 PV 攝影機轉譯可提供下列對預設 MRC 體驗的改良功能:</span><span class="sxs-lookup"><span data-stu-id="024c8-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="024c8-129">您的實體環境和手上的全像投影對齊 (用於近距離互動) 應會隨時精確, 而不是在焦點點以外的距離 (如您在預設的 MRC 中看到)。</span><span class="sxs-lookup"><span data-stu-id="024c8-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="024c8-130">耳機中的適當眼睛不會受到危害, 因為它不會用來呈現 MRC 輸出的全息影像。</span><span class="sxs-lookup"><span data-stu-id="024c8-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="024c8-131">有三個步驟可讓您從 PV 攝影機進行轉譯:</span><span class="sxs-lookup"><span data-stu-id="024c8-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="024c8-132">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="024c8-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="024c8-133">處理其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="024c8-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="024c8-134">確認您的著色器和程式碼從這個額外的 HolographicCamera 正確呈現</span><span class="sxs-lookup"><span data-stu-id="024c8-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="024c8-135">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="024c8-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="024c8-136">若要加入宣告, 應用程式只會啟用 PhotoVideoCamera 的[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="024c8-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="024c8-137">處理 DirectX 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="024c8-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="024c8-138">當應用程式選擇從 PV 攝影機轉譯時, 混合現實 capture 就會開始:</span><span class="sxs-lookup"><span data-stu-id="024c8-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="024c8-139">HolographicSpace 的 CameraAdded 事件將會引發。</span><span class="sxs-lookup"><span data-stu-id="024c8-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="024c8-140">如果應用程式目前無法處理相機, 此事件可能會延遲。</span><span class="sxs-lookup"><span data-stu-id="024c8-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="024c8-141">一旦事件完成 (而且沒有任何未完成的延期), HolographicCamera 就會出現在下一個 HolographicFrame 的 [AddedCameras] 清單中。</span><span class="sxs-lookup"><span data-stu-id="024c8-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="024c8-142">當混合現實 capture 停止時 (或如果應用程式在混合現實 capture 執行時停用 view 設定): HolographicCamera 會出現在下一個 HolographicFrame 的 RemovedCameras 清單中, 而 HolographicSpace 的 CameraRemoved 事件將會從中.</span><span class="sxs-lookup"><span data-stu-id="024c8-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="024c8-143">已將[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)屬性新增至 HolographicCamera, 以協助識別相機所屬的設定。</span><span class="sxs-lookup"><span data-stu-id="024c8-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="024c8-144">處理 Unity 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="024c8-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="024c8-145">從 PV 攝影機轉譯的 Unity 支援正在開發中, 尚無法使用。</span><span class="sxs-lookup"><span data-stu-id="024c8-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="024c8-146">當支援從 PV 攝影機轉譯的 Unity 組建可供使用時, 將會更新這份檔。</span><span class="sxs-lookup"><span data-stu-id="024c8-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="024c8-147">驗證著色器和程式碼支援其他相機</span><span class="sxs-lookup"><span data-stu-id="024c8-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="024c8-148">執行混合的現實捕捉, 並檢查是否有不尋常的對齊、遺失的內容或效能問題。</span><span class="sxs-lookup"><span data-stu-id="024c8-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="024c8-149">適當地更新著色器和程式碼。</span><span class="sxs-lookup"><span data-stu-id="024c8-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="024c8-150">如果有某些場景無法支援轉譯為其他相機, 您可以在 PhotoVideoCamera 的 HolographicViewConfiguration 期間停用它。</span><span class="sxs-lookup"><span data-stu-id="024c8-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="024c8-151">在您的應用程式中停用 MRC</span><span class="sxs-lookup"><span data-stu-id="024c8-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="024c8-152">2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="024c8-152">2D app</span></span>

<span data-ttu-id="024c8-153">2D 應用程式可以選擇在執行混合現實 capture 時, 將其視覺內容遮蔽:</span><span class="sxs-lookup"><span data-stu-id="024c8-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="024c8-154">以[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)旗標呈現</span><span class="sxs-lookup"><span data-stu-id="024c8-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="024c8-155">使用[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)旗標來建立應用程式的交換鏈</span><span class="sxs-lookup"><span data-stu-id="024c8-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="024c8-156">使用 Windows 10 5 月2019更新, 設定 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="024c8-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="024c8-157">沉浸式應用程式</span><span class="sxs-lookup"><span data-stu-id="024c8-157">Immersive app</span></span>

<span data-ttu-id="024c8-158">沉浸式應用程式可以選擇從混合現實 capture 中排除其視覺內容, 方法如下:</span><span class="sxs-lookup"><span data-stu-id="024c8-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="024c8-159">將 HolographicCameraRenderingParameter 的[IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)設定為停用其相關聯框架的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="024c8-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="024c8-160">將 HolographicCamera 的[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)設定為停用其相關聯的全像攝影攝影機的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="024c8-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="024c8-161">密碼鍵盤</span><span class="sxs-lookup"><span data-stu-id="024c8-161">Password Keyboard</span></span>

<span data-ttu-id="024c8-162">有了 Windows 10 的2019更新, 當顯示密碼或 pin 鍵盤時, 視覺內容會自動從混合現實 capture 中排除。</span><span class="sxs-lookup"><span data-stu-id="024c8-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="024c8-163">瞭解 MRC 何時處於作用中</span><span class="sxs-lookup"><span data-stu-id="024c8-163">Knowing when MRC is active</span></span>

<span data-ttu-id="024c8-164">應用程式可以使用[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別來知道何時執行系統混合現實 capture (針對音訊或影片)。</span><span class="sxs-lookup"><span data-stu-id="024c8-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="024c8-165">如果裝置上無法使用混合現實捕捉, AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="024c8-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="024c8-166">也請務必在應用程式暫停時, 取消註冊 CapturingChanged 事件, 否則 MRC 可能會進入封鎖狀態。</span><span class="sxs-lookup"><span data-stu-id="024c8-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="024c8-167">最佳做法 (HoloLens 特定)</span><span class="sxs-lookup"><span data-stu-id="024c8-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="024c8-168">MRC 預期不需要開發人員執行其他工作, 但有幾件事要注意, 以提供應用程式的最佳混合現實捕捉體驗。</span><span class="sxs-lookup"><span data-stu-id="024c8-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="024c8-169">**MRC 使用全息圖形的 Alpha 色板與[相機](locatable-camera.md)影像混合**</span><span class="sxs-lookup"><span data-stu-id="024c8-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="024c8-170">最重要的步驟是確定您的應用程式已清除為透明黑色, 而不是清除為不透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="024c8-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="024c8-171">在 Unity 中, 這是根據 MixedRealityToolkit 的預設值, 但如果您是在非 Unity 中進行開發, 您可能需要變更一行。</span><span class="sxs-lookup"><span data-stu-id="024c8-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="024c8-172">如果您的應用程式未清除為透明黑色, 以下是您可能會在 MRC 中看到的一些成品:</span><span class="sxs-lookup"><span data-stu-id="024c8-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="024c8-173">**失敗的範例**:內容周圍的黑色邊緣 (無法清除為透明黑色)</span><span class="sxs-lookup"><span data-stu-id="024c8-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="024c8-174">**失敗的範例**:全像投影的整個背景場景會呈現黑色。</span><span class="sxs-lookup"><span data-stu-id="024c8-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="024c8-175">將背景 Alpha 值設定為1會導致黑色背景</span><span class="sxs-lookup"><span data-stu-id="024c8-175">Setting a background alpha value of 1 results in a black background</span></span>

![將背景 Alpha 值設定為1會導致黑色背景](images/clearopaqueblack-300px.png)

<span data-ttu-id="024c8-177">**預期的結果**:全息影像與真實世界有適當的混合 (如果清除為透明黑色, 則預期會產生結果)</span><span class="sxs-lookup"><span data-stu-id="024c8-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![清除透明黑色時的預期結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="024c8-179">**解決方案**：</span><span class="sxs-lookup"><span data-stu-id="024c8-179">**Solution**:</span></span>
* <span data-ttu-id="024c8-180">將顯示為不透明黑色的任何內容變更為具有 Alpha 值0。</span><span class="sxs-lookup"><span data-stu-id="024c8-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="024c8-181">確定應用程式已清除為透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="024c8-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="024c8-182">Unity 預設為使用 MixedRealityToolkit 自動清除, 但如果它是非 Unity 應用程式, 您應該修改與 ID3D11DeiceCoNtext:: ClearRenderTargetView () 搭配使用的色彩。</span><span class="sxs-lookup"><span data-stu-id="024c8-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="024c8-183">您想要確保清除透明的黑色 (0, 0, 0, 0), 而不是不透明的黑色 (0, 0, 0, 1)。</span><span class="sxs-lookup"><span data-stu-id="024c8-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="024c8-184">如有需要, 您現在可以微調資產的 Alpha 值, 但通常不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="024c8-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="024c8-185">在大部分的情況下, MRCs 看起來都很好用。</span><span class="sxs-lookup"><span data-stu-id="024c8-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="024c8-186">MRC 會假設已乘以 Alpha。</span><span class="sxs-lookup"><span data-stu-id="024c8-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="024c8-187">Alpha 值只會影響 MRC 捕捉。</span><span class="sxs-lookup"><span data-stu-id="024c8-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="024c8-188">在 HoloLens 上啟用 MRC 時的預期事項</span><span class="sxs-lookup"><span data-stu-id="024c8-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="024c8-189">以下適用于 HoloLens (第一代) 和 HoloLens 2, 除非另有注明:</span><span class="sxs-lookup"><span data-stu-id="024c8-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="024c8-190">系統會將應用程式節流以30Hz 轉譯。</span><span class="sxs-lookup"><span data-stu-id="024c8-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="024c8-191">這會建立一些可供 MRC 執行的空間, 因此應用程式不需要保留持續的預算保留, 而且也會符合30fps 的 MRC 影片記錄的畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="024c8-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="024c8-192">在錄製/串流處理 MRC 時, 裝置上的全息影像內容可能會顯示為「閃爍」: 文字可能會變得更難以閱讀, 而全息全像投影邊緣可能會更 jaggy (在**HoloLens 2**上選擇第三張攝影機轉譯可避免這種危害)</span><span class="sxs-lookup"><span data-stu-id="024c8-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="024c8-193">如果應用程式已啟用「MRC 相片」和「影片」, 將會遵循該應用程式的[焦點](focus-point-in-unity.md), 這有助於確保全息影像的位置正確。</span><span class="sxs-lookup"><span data-stu-id="024c8-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="024c8-194">針對影片, 焦點會平滑, 因此如果焦點深度改變, 則全息影像可能會變得緩慢。</span><span class="sxs-lookup"><span data-stu-id="024c8-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="024c8-195">從焦點點不同深度的全息影像可能會顯示在現實世界中的位移 (請參閱下列範例, 其中的焦點是設定為2個計量, 但全息全像是位於1個計量)。</span><span class="sxs-lookup"><span data-stu-id="024c8-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![以2計的全息影像會完全向世界註冊。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="024c8-198">從您的應用程式內整合 MRC 功能</span><span class="sxs-lookup"><span data-stu-id="024c8-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="024c8-199">您的混合現實應用程式可以從應用程式內起始 MRC 相片或影片捕捉, 而所捕捉到的內容則會提供給您的應用程式使用, 而不會儲存至裝置的「相機變換」。</span><span class="sxs-lookup"><span data-stu-id="024c8-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="024c8-200">您可以建立自訂的「MRC 錄製器」, 或利用內建的「相機捕捉」 UI。</span><span class="sxs-lookup"><span data-stu-id="024c8-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="024c8-201">具有內建攝影機 UI 的 MRC</span><span class="sxs-lookup"><span data-stu-id="024c8-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="024c8-202">開發人員可以使用 *[相機擷取 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 取得的使用者擷取混合的實境相片或視訊，只要短短幾行程式碼。</span><span class="sxs-lookup"><span data-stu-id="024c8-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="024c8-203">此 API 會啟動內建的 MRC 攝影機 UI, 讓使用者可以在其中拍攝相片或影片, 並將產生的 capture 傳回給您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="024c8-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="024c8-204">如果您想要建立自己的相機 UI, 或需要較低層級的 capture 串流存取, 您可以建立自訂的混合現實「捕捉錄製器」。</span><span class="sxs-lookup"><span data-stu-id="024c8-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="024c8-205">建立自訂的「MRC 錄製器」</span><span class="sxs-lookup"><span data-stu-id="024c8-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="024c8-206">雖然使用者一律可以使用系統 MRC 捕捉服務觸發相片或影片, 但應用程式可能會想要建立自訂相機應用程式, 但在相機串流中包含全息影像, 就像 MRC 一樣。</span><span class="sxs-lookup"><span data-stu-id="024c8-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="024c8-207">這可讓應用程式代表使用者啟動捕捉、建立自訂錄製 UI, 或自訂 MRC 設定來命名一些範例。</span><span class="sxs-lookup"><span data-stu-id="024c8-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="024c8-208">**HoloStudio 使用 MRC 效果新增自訂的 MRC 相機**</span><span class="sxs-lookup"><span data-stu-id="024c8-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 使用 MRC 效果新增自訂的 MRC 相機](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="024c8-210">Unity 應用程式應該會看到屬性的[Locatable_camera_in_Unity](locatable-camera-in-unity.md) , 以啟用全息影像。</span><span class="sxs-lookup"><span data-stu-id="024c8-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="024c8-211">其他應用程式可以使用[Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相機並新增 MRC 影片和音訊效果, 以在靜止和影片中包含虛擬的全息影像和應用程式音訊, 來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="024c8-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="024c8-212">應用程式有兩個選項可新增效果:</span><span class="sxs-lookup"><span data-stu-id="024c8-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="024c8-213">舊版 API:[MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="024c8-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="024c8-214">新的 Microsoft 建議 API (會傳回物件, 讓您能夠操作動態屬性):[MediaCapture. AddVideoEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture AddAudioEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) , 它會要求應用程式建立自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)執行, 以及[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。</span><span class="sxs-lookup"><span data-stu-id="024c8-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="024c8-215">如需範例使用方式, 請參閱 MRC 效果範例。</span><span class="sxs-lookup"><span data-stu-id="024c8-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="024c8-216">Visual Studio 將無法辨識 MixedRealityCapture 命名空間, 但字串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="024c8-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="024c8-217">MRC 影片效果 (**Windows. MixedRealityCapture. MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="024c8-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="024c8-218">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="024c8-218">Property Name</span></span>  |  <span data-ttu-id="024c8-219">Type</span><span class="sxs-lookup"><span data-stu-id="024c8-219">Type</span></span>  |  <span data-ttu-id="024c8-220">Default Value</span><span class="sxs-lookup"><span data-stu-id="024c8-220">Default Value</span></span>  |  <span data-ttu-id="024c8-221">描述</span><span class="sxs-lookup"><span data-stu-id="024c8-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="024c8-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="024c8-222">StreamType</span></span>  |  <span data-ttu-id="024c8-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="024c8-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="024c8-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="024c8-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="024c8-225">描述此效果用於哪一個捕捉串流。</span><span class="sxs-lookup"><span data-stu-id="024c8-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="024c8-226">音訊無法使用。</span><span class="sxs-lookup"><span data-stu-id="024c8-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="024c8-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="024c8-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="024c8-228">boolean</span><span class="sxs-lookup"><span data-stu-id="024c8-228">boolean</span></span>  |  <span data-ttu-id="024c8-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="024c8-229">TRUE</span></span>  |  <span data-ttu-id="024c8-230">用來啟用或停用影片捕捉中的全息影像的旗標。</span><span class="sxs-lookup"><span data-stu-id="024c8-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="024c8-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="024c8-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="024c8-232">boolean</span><span class="sxs-lookup"><span data-stu-id="024c8-232">boolean</span></span>  |  <span data-ttu-id="024c8-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="024c8-233">TRUE</span></span>  |  <span data-ttu-id="024c8-234">用來啟用或停用在全息影像捕捉期間錄製指示器的旗標。</span><span class="sxs-lookup"><span data-stu-id="024c8-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="024c8-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="024c8-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="024c8-236">boolean</span><span class="sxs-lookup"><span data-stu-id="024c8-236">boolean</span></span>  |  <span data-ttu-id="024c8-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="024c8-237">FALSE</span></span>  |  <span data-ttu-id="024c8-238">用來啟用或停用 HoloLens 追蹤程式所支援之視頻穩定的旗標。</span><span class="sxs-lookup"><span data-stu-id="024c8-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="024c8-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="024c8-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="024c8-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="024c8-240">UINT32</span></span>  |  <span data-ttu-id="024c8-241">0</span><span class="sxs-lookup"><span data-stu-id="024c8-241">0</span></span>  |  <span data-ttu-id="024c8-242">設定用於視頻穩定的歷程記錄畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="024c8-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="024c8-243">從電源和效能的角度來看, 0 為 0-延遲, 幾乎是「免費」。</span><span class="sxs-lookup"><span data-stu-id="024c8-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="024c8-244">15是建議的最高品質 (以延遲和記憶體15個畫面的成本為代價)。</span><span class="sxs-lookup"><span data-stu-id="024c8-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="024c8-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="024c8-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="024c8-246">FLOAT</span><span class="sxs-lookup"><span data-stu-id="024c8-246">float</span></span>  |  <span data-ttu-id="024c8-247">0.9 (HoloLens) 1.0 (沉浸式耳機)</span><span class="sxs-lookup"><span data-stu-id="024c8-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="024c8-248">設定從 0.0 (完全透明) 到 1.0 (完全不透明) 範圍內的全息影像全域不透明度係數。</span><span class="sxs-lookup"><span data-stu-id="024c8-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="024c8-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="024c8-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="024c8-250">boolean</span><span class="sxs-lookup"><span data-stu-id="024c8-250">boolean</span></span>  |  <span data-ttu-id="024c8-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="024c8-251">FALSE</span></span>  |  <span data-ttu-id="024c8-252">當有 2d UWP 應用程式顯示受保護的內容時, 啟用或停用的旗標會傳回空白框架。</span><span class="sxs-lookup"><span data-stu-id="024c8-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="024c8-253">如果此旗標為 false, 而 2d UWP 應用程式顯示受保護的內容, 則 2d UWP 應用程式將會被耳機和混合現實捕捉中的受保護內容材質取代。</span><span class="sxs-lookup"><span data-stu-id="024c8-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="024c8-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="024c8-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="024c8-255">boolean</span><span class="sxs-lookup"><span data-stu-id="024c8-255">boolean</span></span>  |  <span data-ttu-id="024c8-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="024c8-256">FALSE</span></span>  |  <span data-ttu-id="024c8-257">用來啟用或停用顯示全像攝影機的隱藏區網格和鄰近內容的旗標。</span><span class="sxs-lookup"><span data-stu-id="024c8-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="024c8-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="024c8-258">OutputSize</span></span> | <span data-ttu-id="024c8-259">Size</span><span class="sxs-lookup"><span data-stu-id="024c8-259">Size</span></span> | <span data-ttu-id="024c8-260">0、0</span><span class="sxs-lookup"><span data-stu-id="024c8-260">0, 0</span></span> | <span data-ttu-id="024c8-261">在裁剪影片穩定之後, 設定所需的輸出大小。</span><span class="sxs-lookup"><span data-stu-id="024c8-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="024c8-262">如果指定0或不正確輸出大小, 則會選擇預設的裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="024c8-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="024c8-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="024c8-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="024c8-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="024c8-264">UINT32</span></span> | <span data-ttu-id="024c8-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="024c8-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="024c8-266">列舉, 用來指出應該捕捉的全像攝影視圖設定。</span><span class="sxs-lookup"><span data-stu-id="024c8-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="024c8-267">設定 0 (顯示) 表示不會要求應用程式從相片/攝影機呈現</span><span class="sxs-lookup"><span data-stu-id="024c8-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="024c8-268">MRC 音訊效果 (**Windows MixedRealityCapture. MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="024c8-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="024c8-269">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="024c8-269">Property Name</span></span></th>
<th><span data-ttu-id="024c8-270">Type</span><span class="sxs-lookup"><span data-stu-id="024c8-270">Type</span></span></th>
<th><span data-ttu-id="024c8-271">Default Value</span><span class="sxs-lookup"><span data-stu-id="024c8-271">Default Value</span></span></th>
<th><span data-ttu-id="024c8-272">描述</span><span class="sxs-lookup"><span data-stu-id="024c8-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="024c8-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="024c8-273">MixerMode</span></span></td>
<td><span data-ttu-id="024c8-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="024c8-274">UINT32</span></span></td>
<td><span data-ttu-id="024c8-275">2</span><span class="sxs-lookup"><span data-stu-id="024c8-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="024c8-276">0僅限 Mic 音訊</span><span class="sxs-lookup"><span data-stu-id="024c8-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="024c8-277">sha-1僅限系統音訊</span><span class="sxs-lookup"><span data-stu-id="024c8-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="024c8-278">2Mic 和系統音訊</span><span class="sxs-lookup"><span data-stu-id="024c8-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="024c8-279">同時 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="024c8-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="024c8-280">同時存取 MRC 的多個應用程式有某些限制。</span><span class="sxs-lookup"><span data-stu-id="024c8-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="024c8-281">相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="024c8-281">Photo/video camera access</span></span>

<span data-ttu-id="024c8-282">相片/攝影機僅限於可以同時存取它的進程數目。</span><span class="sxs-lookup"><span data-stu-id="024c8-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="024c8-283">當處理常式正在錄製影片或拍攝相片時, 任何其他程式將無法取得相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="024c8-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="024c8-284">(這同時適用于混合現實捕捉和標準相片/影片捕捉)</span><span class="sxs-lookup"><span data-stu-id="024c8-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="024c8-285">使用 HoloLens 2, 應用程式可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)內容來指出, 如果他們不需要對相片/攝影機進行獨佔控制, 他們想要執行 SharedReadOnly。</span><span class="sxs-lookup"><span data-stu-id="024c8-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="024c8-286">這麼做表示, 捕捉的解析度和畫面播放速率會限制為其他應用程式已設定相機提供的功能。</span><span class="sxs-lookup"><span data-stu-id="024c8-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="024c8-287">內建的 MRC 相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="024c8-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="024c8-288">Windows 10 內建的 MRC 功能 (透過 Cortana、[開始] 功能表、硬體快捷方式、Miracast、Windows 裝置入口網站):</span><span class="sxs-lookup"><span data-stu-id="024c8-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="024c8-289">預設會以 ExclusiveControl 執行</span><span class="sxs-lookup"><span data-stu-id="024c8-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="024c8-290">不過, 已將支援新增至每個子系統, 以共用模式運作:</span><span class="sxs-lookup"><span data-stu-id="024c8-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="024c8-291">如果應用程式要求相片/攝影機的 ExclusiveControl 存取權, 內建的 MRC 會自動停止使用相片/攝影機, 讓應用程式的要求成功</span><span class="sxs-lookup"><span data-stu-id="024c8-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="024c8-292">如果在應用程式有 ExclusiveControl 時啟動內建的 MRC, 內建的 MRC 會在 SharedReadOnly 模式中執行</span><span class="sxs-lookup"><span data-stu-id="024c8-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="024c8-293">此共用模式功能有一些限制:</span><span class="sxs-lookup"><span data-stu-id="024c8-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="024c8-294">透過 Cortana、硬體快捷方式或 [開始] 功能表的相片:需要 Windows 10 2018 年4月更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="024c8-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="024c8-295">透過 Cortana、硬體快捷方式或 [開始] 功能表的影片:需要 Windows 10 2018 年4月更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="024c8-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="024c8-296">透過 Miracast 的串流處理 MRC:需要 Windows 10 2018 年10月更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="024c8-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="024c8-297">透過 Windows 裝置入口網站或透過 HoloLens 隨附應用程式來串流處理 MRC:需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="024c8-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="024c8-298">當另一個應用程式正在使用相片/攝影機時, 內建 MRC 相機 UI 的解析度和畫面播放速率可能會從其正常值中縮減。</span><span class="sxs-lookup"><span data-stu-id="024c8-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="024c8-299">MRC 存取</span><span class="sxs-lookup"><span data-stu-id="024c8-299">MRC access</span></span>

<span data-ttu-id="024c8-300">在 Windows 10 四月份2018更新中, 有多個應用程式存取 MRC 串流不再受限制 (不過, 相片/攝影機的存取仍然有限制)。</span><span class="sxs-lookup"><span data-stu-id="024c8-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="024c8-301">在 Windows 10 4 月2018更新之前, 應用程式的自訂 MRC 錄製器與系統 MRC (從 Windows 裝置入口網站捕捉相片、捕獲影片或串流) 互斥。</span><span class="sxs-lookup"><span data-stu-id="024c8-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="024c8-302">另請參閱</span><span class="sxs-lookup"><span data-stu-id="024c8-302">See also</span></span>
* [<span data-ttu-id="024c8-303">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="024c8-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="024c8-304">觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="024c8-304">Spectator view</span></span>](spectator-view.md)
