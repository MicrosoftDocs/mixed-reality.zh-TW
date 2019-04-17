---
title: Spectator 檢視
description: 將外部裝置從全像投影視覺化做為示範的外部顯示器上的混合的實境體驗或錄製視訊的混合的實境體驗。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator 檢視中，資料 iPhone、 iPad iOS OpenCV、 相機、 ARKit、 HoloLens、 混合實境、 MixedRealityToolkit，示範中，記錄
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595414"
---
# <a name="spectator-view-for-hololens"></a><span data-ttu-id="7f3e4-104">HoloLens spectator 檢視</span><span class="sxs-lookup"><span data-stu-id="7f3e4-104">Spectator View for HoloLens</span></span>

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a><span data-ttu-id="7f3e4-106">目前的重構</span><span class="sxs-lookup"><span data-stu-id="7f3e4-106">Current Refactor</span></span>

> [!NOTE]
><span data-ttu-id="7f3e4-107">正在主動重構 HoloLens spectator 檢視。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-107">Spectator View for HoloLens is being actively refactored.</span></span> <span data-ttu-id="7f3e4-108">這項工作要合併的預覽和 Pro 程式碼基底，並將支援延伸到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-108">This work is intended to consolidate the Preview and Pro codebases and extend support to HoloLens 2.</span></span> 

<span data-ttu-id="7f3e4-109">若要檢視目前 Spectator 檢視重構的狀態，請參閱 MixedRealityToolkit 和 MixedRealityToolkit Unity 的存放庫中的 '功能/spectatorView' 分支：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-109">To view the current state of the Spectator View refactor see 'feature/spectatorView' branches in both the MixedRealityToolkit and MixedRealityToolkit-Unity repos:</span></span>

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

<span data-ttu-id="7f3e4-110">和</span><span class="sxs-lookup"><span data-stu-id="7f3e4-110">and</span></span>

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a><span data-ttu-id="7f3e4-111">總覽</span><span class="sxs-lookup"><span data-stu-id="7f3e4-111">Overview</span></span>

<span data-ttu-id="7f3e4-112">當穿著 HoloLens，我們常常忘了，個人使用者不具有它是無法體驗，我們可以。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-112">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="7f3e4-113">Spectator 檢視可讓其他人在 2D 螢幕上看到 HoloLens 使用者會看到他們的世界中。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-113">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="7f3e4-114">Spectator 檢視 （預覽） 是快速且經濟實惠方式 HD 中錄製全像投影，而 Spectator 檢視 Pro 適用於專業品質的全像投影的記錄。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-114">Spectator View (Preview) is fast and affordable approach to recording holograms in HD, while Spectator View Pro is intended for professional quality recording of holograms.</span></span>

<span data-ttu-id="7f3e4-115">下表顯示的選項和其功能。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-115">The following table shows both options and their capabilities.</span></span> <span data-ttu-id="7f3e4-116">選擇最適合您的視訊錄製需求的選項：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-116">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="7f3e4-117">Spectator 檢視 （預覽）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-117">Spectator View (Preview)</span></span> |              <span data-ttu-id="7f3e4-118">Spectator 檢視 Pro</span><span class="sxs-lookup"><span data-stu-id="7f3e4-118">Spectator View Pro</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="7f3e4-119">HD 品質</span><span class="sxs-lookup"><span data-stu-id="7f3e4-119">HD quality</span></span>                         |         <span data-ttu-id="7f3e4-120">Full HD</span><span class="sxs-lookup"><span data-stu-id="7f3e4-120">Full HD</span></span>         |        <span data-ttu-id="7f3e4-121">專業品質 filming （如同取決於 DSLR）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-121">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="7f3e4-122">簡單的觀景窗移動</span><span class="sxs-lookup"><span data-stu-id="7f3e4-122">Easy camera movement</span></span>                      |            <span data-ttu-id="7f3e4-123">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-123">✔</span></span>            |                                             |
| <span data-ttu-id="7f3e4-124">第三位使用者檢視</span><span class="sxs-lookup"><span data-stu-id="7f3e4-124">Third-person view</span></span>                    |            <span data-ttu-id="7f3e4-125">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-125">✔</span></span>            |                      <span data-ttu-id="7f3e4-126">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-126">✔</span></span>                      |
| <span data-ttu-id="7f3e4-127">可以將串流處理至螢幕</span><span class="sxs-lookup"><span data-stu-id="7f3e4-127">Can be streamed to screens</span></span>           |            <span data-ttu-id="7f3e4-128">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-128">✔</span></span>            |                      <span data-ttu-id="7f3e4-129">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-129">✔</span></span>                      |
| <span data-ttu-id="7f3e4-130">可攜式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-130">Portable</span></span>                             |            <span data-ttu-id="7f3e4-131">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-131">✔</span></span>            |                                             |
| <span data-ttu-id="7f3e4-132">無線</span><span class="sxs-lookup"><span data-stu-id="7f3e4-132">Wireless</span></span>                             |            <span data-ttu-id="7f3e4-133">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-133">✔</span></span>            |                                             |
| <span data-ttu-id="7f3e4-134">其他必要的硬體</span><span class="sxs-lookup"><span data-stu-id="7f3e4-134">Additional required hardware</span></span>         |     <span data-ttu-id="7f3e4-135">iPhone （或 iPad）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-135">iPhone (or iPad)</span></span>    | <span data-ttu-id="7f3e4-136">HoloLens + Rig + 三腳架 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="7f3e4-136">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="7f3e4-137">硬體投資</span><span class="sxs-lookup"><span data-stu-id="7f3e4-137">Hardware investment</span></span>                  |           <span data-ttu-id="7f3e4-138">低</span><span class="sxs-lookup"><span data-stu-id="7f3e4-138">Low</span></span>           |                     <span data-ttu-id="7f3e4-139">高</span><span class="sxs-lookup"><span data-stu-id="7f3e4-139">High</span></span>                    |
| <span data-ttu-id="7f3e4-140">跨平台</span><span class="sxs-lookup"><span data-stu-id="7f3e4-140">Cross-platform</span></span>                       |           <span data-ttu-id="7f3e4-141">iOS</span><span class="sxs-lookup"><span data-stu-id="7f3e4-141">iOS</span></span>           |                                             |
| <span data-ttu-id="7f3e4-142">檢視器可以互動</span><span class="sxs-lookup"><span data-stu-id="7f3e4-142">Viewer can interact</span></span>                  |            <span data-ttu-id="7f3e4-143">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-143">✔</span></span>            |                                             |
| <span data-ttu-id="7f3e4-144">網路功能的所需 （UNET 指令碼）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-144">Networking required (UNET scripting)</span></span> |            <span data-ttu-id="7f3e4-145">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-145">✔</span></span>            |                      <span data-ttu-id="7f3e4-146">✔</span><span class="sxs-lookup"><span data-stu-id="7f3e4-146">✔</span></span>                      |
| <span data-ttu-id="7f3e4-147">執行階段安裝程式的持續時間</span><span class="sxs-lookup"><span data-stu-id="7f3e4-147">Runtime setup duration</span></span>               |         <span data-ttu-id="7f3e4-148">即時</span><span class="sxs-lookup"><span data-stu-id="7f3e4-148">Instant</span></span>         |                     <span data-ttu-id="7f3e4-149">慢速</span><span class="sxs-lookup"><span data-stu-id="7f3e4-149">Slow</span></span>                    |

## <a name="spectator-view-preview"></a><span data-ttu-id="7f3e4-150">Spectator 檢視 （預覽）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-150">Spectator View (Preview)</span></span>

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a><span data-ttu-id="7f3e4-152">使用案例</span><span class="sxs-lookup"><span data-stu-id="7f3e4-152">Use cases</span></span>

- <span data-ttu-id="7f3e4-153">Filming HD 中的全像投影：您可以使用 Spectator 檢視 （預覽），來記錄使用 iPhone 的混合的實境體驗。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-153">Filming holograms in HD: Using Spectator View (Preview), you can record a mixed reality experience using an iPhone.</span></span> <span data-ttu-id="7f3e4-154">在 full HD 中記錄，並將消除鋸齒套用至全像投影和甚至陰影。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-154">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="7f3e4-155">這是符合成本效益且快速的方式來擷取影片的全像投影。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-155">It is a cost-effective and quick way to capture video of holograms.</span></span>
- <span data-ttu-id="7f3e4-156">即時示範：Stream 即時混合的實境體驗至 Apple TV 直接從 iPhone 或 iPad，延隔時間-免費 ！</span><span class="sxs-lookup"><span data-stu-id="7f3e4-156">Live demos: Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
- <span data-ttu-id="7f3e4-157">來賓分享您的經驗：可讓非 HoloLens 使用者體驗全像投影直接從他們的手機或平板電腦。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-157">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

### <a name="current-features"></a><span data-ttu-id="7f3e4-158">目前的功能</span><span class="sxs-lookup"><span data-stu-id="7f3e4-158">Current features</span></span>

- <span data-ttu-id="7f3e4-159">網路自動搜索功能將電話新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-159">Network auto-discovery for adding phones to the session.</span></span>
- <span data-ttu-id="7f3e4-160">自動的工作階段處理，因此使用者會新增至正確的工作階段。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-160">Automatic session handling, so users are added to the correct session.</span></span>
- <span data-ttu-id="7f3e4-161">同步處理空間全像投影，因此所有人會看到全像投影中完全相同的位置。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-161">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
- <span data-ttu-id="7f3e4-162">podpora iOS pro （ARKit 功能的裝置）。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-162">iOS support (ARKit-enabled devices).</span></span>
- <span data-ttu-id="7f3e4-163">多個 iOS 來賓。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-163">Multiple iOS guests.</span></span>
- <span data-ttu-id="7f3e4-164">錄製的視訊 + 全像投影 + 環境的聲音 + 全像音效。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-164">Recording of video + holograms + ambient sound + hologram sound.</span></span>
- <span data-ttu-id="7f3e4-165">共用工作表，因此您可以儲存影片、 電子郵件，或與其他支援的應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-165">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>


>[!NOTE] 
><span data-ttu-id="7f3e4-166">Spectator 檢視 （預覽） 程式碼無法搭配 Spectator 檢視 Pro 版本程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-166">The Spectator View (Preview) code cannot be used with the Spectator View Pro version code.</span></span> <span data-ttu-id="7f3e4-167">我們建議在新的專案需要視訊錄製全像投影的情況中加以實作。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-167">We recommend to implement it in new projects where video recording of holograms is required.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a><span data-ttu-id="7f3e4-168">授權</span><span class="sxs-lookup"><span data-stu-id="7f3e4-168">Licenses</span></span>

- [<span data-ttu-id="7f3e4-169">OpenCV-（3 子句 BSD 授權）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-169">OpenCV - (3-clause BSD License)</span></span>](https://opencv.org/license.html)
- [<span data-ttu-id="7f3e4-170">Unity ARKit-（MIT 授權）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-170">Unity ARKit - (MIT License)</span></span>](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a><span data-ttu-id="7f3e4-171">如何設定 Spectator 檢視 （預覽）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-171">How to set up Spectator View (Preview)</span></span>

### <a name="requirements"></a><span data-ttu-id="7f3e4-172">需求</span><span class="sxs-lookup"><span data-stu-id="7f3e4-172">Requirements</span></span>

- <span data-ttu-id="7f3e4-173">[Spectator 檢視外掛程式和必要的 OpenCV 二進位檔](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-如何建置 Spectator 檢視原生外掛程式的詳細資訊，請參閱下方。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-173">[Spectator View plugin and required OpenCV binaries](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) - Details on how to build the Spectator View Native Plugin can be found below.</span></span> <span data-ttu-id="7f3e4-174">從產生的二進位檔，您將需要︰</span><span class="sxs-lookup"><span data-stu-id="7f3e4-174">From the generated binaries you will need:</span></span>

    - <span data-ttu-id="7f3e4-175">opencv_aruco343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-175">opencv_aruco343.dll</span></span>
    - <span data-ttu-id="7f3e4-176">opencv_calib3d343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-176">opencv_calib3d343.dll</span></span>
    - <span data-ttu-id="7f3e4-177">opencv_core343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-177">opencv_core343.dll</span></span>
    - <span data-ttu-id="7f3e4-178">opencv_features2d343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-178">opencv_features2d343.dll</span></span>
    - <span data-ttu-id="7f3e4-179">opencv_flann343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-179">opencv_flann343.dll</span></span>
    - <span data-ttu-id="7f3e4-180">opencv_imgproc343.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-180">opencv_imgproc343.dll</span></span>

    - <span data-ttu-id="7f3e4-181">zlib1.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-181">zlib1.dll</span></span>
    - <span data-ttu-id="7f3e4-182">SpectatorViewPlugin.dll</span><span class="sxs-lookup"><span data-stu-id="7f3e4-182">SpectatorViewPlugin.dll</span></span>
- <span data-ttu-id="7f3e4-183">Spectator 檢視會使用 Unity 網路功能 (UNET) 及其網路探索和空間的同步處理。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-183">Spectator View uses Unity Networking (UNET) for its network discovery and spatial syncing.</span></span> <span data-ttu-id="7f3e4-184">這表示應用程式時的所有互動性必須在裝置之間進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-184">This means all interactivity during the application needs to be synced between the devices.</span></span>
- <span data-ttu-id="7f3e4-185">Unity 2017.2.1p2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="7f3e4-185">Unity 2017.2.1p2 or later</span></span>
- <span data-ttu-id="7f3e4-186">硬體</span><span class="sxs-lookup"><span data-stu-id="7f3e4-186">Hardware</span></span>
    - <span data-ttu-id="7f3e4-187">HoloLens</span><span class="sxs-lookup"><span data-stu-id="7f3e4-187">A HoloLens</span></span>
    - <span data-ttu-id="7f3e4-188">執行 Windows 10 的 Windows PC</span><span class="sxs-lookup"><span data-stu-id="7f3e4-188">Windows PC running Windows 10</span></span>
    - <span data-ttu-id="7f3e4-189">ARKit 相容的裝置 (iPhone 6s 及更新版本 / iPad Pro 2016 及更新版本 / iPad 2017 及更新版本)-執行 iOS 11 或更高版本</span><span class="sxs-lookup"><span data-stu-id="7f3e4-189">ARKit compatible device (iPhone 6s onwards / iPad Pro 2016 onwards / iPad 2017 onwards) - running iOS 11 or above</span></span>
    - <span data-ttu-id="7f3e4-190">與 xcode 9.2 和更新版本的 Mac</span><span class="sxs-lookup"><span data-stu-id="7f3e4-190">Mac with xcode 9.2 onwards</span></span>
- <span data-ttu-id="7f3e4-191">Apple 開發人員帳戶，免費或[付費](https://developer.apple.com/)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-191">Apple developer account, free or [paid](https://developer.apple.com/)</span></span>
- <span data-ttu-id="7f3e4-192">Microsoft Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7f3e4-192">Microsoft Visual Studio 2017</span></span>

### <a name="building-the-spectator-view-native-plugin"></a><span data-ttu-id="7f3e4-193">建置 Spectator 檢視原生外掛程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-193">Building the Spectator View native plugin</span></span>

<span data-ttu-id="7f3e4-194">若要產生所需的檔案，請遵循下列步驟： https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span><span class="sxs-lookup"><span data-stu-id="7f3e4-194">To generate the required files, follow these steps: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span></span>

### <a name="project-setup"></a><span data-ttu-id="7f3e4-195">專案設定</span><span class="sxs-lookup"><span data-stu-id="7f3e4-195">Project setup</span></span>

1. <span data-ttu-id="7f3e4-196">準備您的場景，請確保場景中的所有可見 gameobject 都包含在全球根 gameobject。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-196">Prepare your scene, ensuring all visable gameobjects within your scene are contained under a world root gameobject.</span></span>

    ![全球根](images/SpecViewPhoneWorldRoot2.PNG)

2. <span data-ttu-id="7f3e4-198">新增 SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 您在場景。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-198">Add the SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) into your scene.</span></span>
3. <span data-ttu-id="7f3e4-199">新增 SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 您在場景。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-199">Add the SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) into your scene.</span></span>
4. <span data-ttu-id="7f3e4-200">選取 SpectatorViewNetworking gameobject 還有 SpectatorViewNetworkingManager 元件，您可以連結的幾件事。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-200">Select the SpectatorViewNetworking gameobject and on the SpectatorViewNetworkingManager component, there's a few things you can link up.</span></span> <span data-ttu-id="7f3e4-201">如果左側不必要的指令碼，在執行階段會搜尋此元件。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-201">If left untouched this component will search for necessary scripts at runtime.</span></span>
    - <span data-ttu-id="7f3e4-202">標記偵測 HoloLens]-> [SpectatorView/Hololens/MarkerDetection</span><span class="sxs-lookup"><span data-stu-id="7f3e4-202">Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection</span></span>
    - <span data-ttu-id="7f3e4-203">標記產生 3D]-> [SpectatorView/IPhone/SyncMarker/3DMarker</span><span class="sxs-lookup"><span data-stu-id="7f3e4-203">Marker Generation 3D -> SpectatorView/IPhone/SyncMarker/3DMarker</span></span>

    ![SpectatorView 網路探索](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a><span data-ttu-id="7f3e4-205">網路應用程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-205">Networking your app</span></span>

- <span data-ttu-id="7f3e4-206">Spectator 檢視 UNET 用於其網路，並管理為您的所有主機用戶端連線。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-206">Spectator View uses UNET for its networking and manages all host-client connections for you.</span></span>
- <span data-ttu-id="7f3e4-207">任何應用程式特定資料，就必須同步，且您使用例如 SyncVars、 NetworkTransform、 NetworkBehavior 實作。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-207">Any app specific data has to be synced and implemented by you, using e.g. SyncVars, NetworkTransform, NetworkBehavior.</span></span>
- <span data-ttu-id="7f3e4-208">如需 Unity 網路功能的詳細資訊請造訪[多人遊戲和網路](https://docs.unity3d.com/Manual/UNet.html)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-208">For more information on Unity Networking please visit [Multiplayer and Networking](https://docs.unity3d.com/Manual/UNet.html).</span></span> <span data-ttu-id="7f3e4-209">(注意：UNet 已被取代;目前的重構 Spectator 檢視程式碼基底會解決此問題）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-209">(Note: UNet has been deprecated; the current refactor of the Spectator View codebase will address this issue)</span></span>

### <a name="building-for-each-platform-hololens-or-ios"></a><span data-ttu-id="7f3e4-210">建立每個平台 （HoloLens 或 iOS）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-210">Building for each platform (HoloLens or iOS)</span></span>

- <span data-ttu-id="7f3e4-211">針對 iOS 建置時，請確定您移除 MRTK GLTF 元件，因為這尚未與此平台相容。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-211">When building for iOS, ensure you remove the GLTF component of MRTK as this is not yet compatible with this platform.</span></span>
- <span data-ttu-id="7f3e4-212">SpectatorView prefab 艟鷁沒有稱為 '平台切換器' 的元件。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-212">At the top level of the SpectatorView prefab there is a component called 'Platform Switcher'.</span></span> <span data-ttu-id="7f3e4-213">選取您想要建置的平台。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-213">Select the platform you want to build for.</span></span>
    - <span data-ttu-id="7f3e4-214">如果選取 'Hololens' 您應該會看到所有 gameobject 下方中變成非使用中 SpectatorView prefab iPhone gameobject 和下 'Hololens' 會變成作用中的所有 gameobject。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-214">If selecting 'Hololens' you should see all gameobjects beneath the iPhone gameobject in the SpectatorView prefab become inactive and all the gameobjects under 'Hololens' become active.</span></span>
    - <span data-ttu-id="7f3e4-215">這可能需要一些時間，視平台在您選擇 HoloToolkit 正在專案中加入或移除。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-215">This can take a little while as depending on the platform you choose the HoloToolkit is being added or removed from the project.</span></span>

    ![平台切換器](images/SpecViewPhoneSwitcher.PNG)

- <span data-ttu-id="7f3e4-217">請確定您建置的應用程式使用相同的 Unity 編輯器執行個體 （執行之間的不關閉 Unity 組建），因為發生未解決的問題，使用 Unity 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-217">Ensure you build all versions of the application using the same Unity editor instance (do not close Unity between builds) due to an unresolved issue with Unity.</span></span>

### <a name="running-your-app"></a><span data-ttu-id="7f3e4-218">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-218">Running your app</span></span>

<span data-ttu-id="7f3e4-219">一旦您建置並部署您應用程式的版本和 HoloLens iPhone 上，您應該能夠將它們連接。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-219">Once you have built and deployed a version of you application on iPhone and on HoloLens, you should be able to connect them.</span></span>

1. <span data-ttu-id="7f3e4-220">請確定這兩個裝置都位於相同的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-220">Ensure that both devices are on the same Wi-Fi network.</span></span>
2. <span data-ttu-id="7f3e4-221">在這兩個裝置，沒有特定順序上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-221">Start the application on the both devices, in no specific order.</span></span> <span data-ttu-id="7f3e4-222">在 iPhone 上啟動應用程式的程序應該會觸發 HoloLens 相機開啟，並開始拍攝相片。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-222">The process of starting the application on the iPhone should trigger the HoloLens camera to turn on and begin taking pictures.</span></span>
3. <span data-ttu-id="7f3e4-223">IPhone 應用程式啟動時，因為它會尋找例如樓層或資料表的介面。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-223">As soon as iPhone app starts, it will look for surfaces like floors or tables.</span></span> <span data-ttu-id="7f3e4-224">當找不到介面時，您應該會看到類似以下的標記。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-224">When surfaces are found, you should see a marker similar to the one below.</span></span> <span data-ttu-id="7f3e4-225">HoloLens 顯示此標記。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-225">Show this marker to the HoloLens.</span></span>

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. <span data-ttu-id="7f3e4-227">一旦偵測到標記應該會消失的 HoloLens 和兩個裝置應該連接，並在空間上同步處理。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-227">Once the marker has been detected by the HoloLens it should disappear and both devices should be connected and spatially synced.</span></span>

### <a name="recording-video"></a><span data-ttu-id="7f3e4-228">錄製影片</span><span class="sxs-lookup"><span data-stu-id="7f3e4-228">Recording video</span></span>

1. <span data-ttu-id="7f3e4-229">若要擷取並儲存從 iPhone 的影片，點選並按住畫面 1 秒。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-229">To capture and save a video from the iPhone, tap and hold the screen for 1 second.</span></span> <span data-ttu-id="7f3e4-230">這會開啟 [記錄] 功能表。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-230">This will open the recording menu.</span></span>
2. <span data-ttu-id="7f3e4-231">點選 [紅色的記錄] 按鈕，這會啟動記錄畫面開始之前的倒數計時。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-231">Tap the red record button, this will start a countdown before beginning to record the screen.</span></span>
3. <span data-ttu-id="7f3e4-232">若要完成錄製點選並按住畫面另一個 1 秒，然後點選 [停止] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-232">To finish recording tap and hold the screen for another 1 second, then tap the stop button.</span></span>
4. <span data-ttu-id="7f3e4-233">錄製的視訊載入之後，會出現 [預覽] 按鈕 （藍色按鈕），請點選要觀賞錄製的視訊。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-233">Once the recorded video loads, a Preview button (blue button) will appear, tap to watch the recorded video.</span></span>
5. <span data-ttu-id="7f3e4-234">開啟共用工作表，選取 儲存至手機相簿。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-234">Open the Share sheet and select Save to camera roll.</span></span>

### <a name="example-scene"></a><span data-ttu-id="7f3e4-235">範例場景</span><span class="sxs-lookup"><span data-stu-id="7f3e4-235">Example scene</span></span>

<span data-ttu-id="7f3e4-236">可以在中找到範例場景[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-236">An example scene can be found in [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="7f3e4-237">疑難排解</span><span class="sxs-lookup"><span data-stu-id="7f3e4-237">Troubleshooting</span></span>

<span data-ttu-id="7f3e4-238">**Unity 編輯器不會連線到 HoloLens 裝置所裝載的工作階段**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-238">**The Unity Editor won't connect to a session hosted by a HoloLens device**</span></span>

- <span data-ttu-id="7f3e4-239">這可能是 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-239">This could be the Windows Firewall.</span></span>
- <span data-ttu-id="7f3e4-240">請移至 [Windows 防火牆] 選項。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-240">Go to Windows Firewall options.</span></span>
- <span data-ttu-id="7f3e4-241">允許應用程式或功能通過 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-241">Allow an app or feature through Windows Firewall.</span></span>
- <span data-ttu-id="7f3e4-242">所有執行個體的 Unity Editor 中清單報價網域、 私人和公用。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-242">For all instances of Unity Editor in the list tick, Domain, Private and Public.</span></span>
- <span data-ttu-id="7f3e4-243">然後移回至 Windows 防火牆 選項。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-243">Then go back to Windows Firewall options.</span></span>
- <span data-ttu-id="7f3e4-244">按一下 進階的設定。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-244">Click Advanced settings.</span></span>
- <span data-ttu-id="7f3e4-245">按一下 [輸入的規則]。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-245">Click Inbound Rules.</span></span>
- <span data-ttu-id="7f3e4-246">在 Unity 編輯器的所有執行個體應該有綠色勾號。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-246">All instances of Unity Editor should have a green tick.</span></span>
- <span data-ttu-id="7f3e4-247">在 Unity 編輯器的任何執行個體，沒有綠色勾號：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-247">For any instances of Unity Editor that don't have a green tick:</span></span>
    - <span data-ttu-id="7f3e4-248">按兩下它。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-248">Double click it.</span></span>
    - <span data-ttu-id="7f3e4-249">在 動作 對話方塊中選取 允許該連線。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-249">In the action dialog select Allow the connection.</span></span>
    - <span data-ttu-id="7f3e4-250">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-250">Click OK.</span></span>
    - <span data-ttu-id="7f3e4-251">重新啟動 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-251">Restart the Unity Editor.</span></span>

<span data-ttu-id="7f3e4-252">**在執行階段 [iPhone] 畫面會顯示 「 尋找 Floor...」但不會顯示 AR 標記。**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-252">**At runtime the iPhone screen says "Locating Floor..." but does not display an AR marker.**</span></span>

- <span data-ttu-id="7f3e4-253">IPhone 正在尋找的水平的介面，因此嘗試指 iPhone 觀景窗朝向最低限度值或資料表。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-253">The iPhone is looking for a horizontal surface so try pointing the iPhone camera towards the floor or a table.</span></span> <span data-ttu-id="7f3e4-254">這有助於 ARKit 尋找在空間上與 HoloLens 的同步處理所需的介面。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-254">This will help ARKit find surfaces necessary to spatially sync with HoloLens.</span></span>

<span data-ttu-id="7f3e4-255">**HoloLens 相機不會開啟自動當 iPhone 嘗試加入。**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-255">**HoloLens camera does not turn on automatically when iPhone tries to join.**</span></span>

- <span data-ttu-id="7f3e4-256">請確定 HoloLens 與 iPhone 相同的 Wi-fi 網路上執行。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-256">Make sure both HoloLens and iPhone are running on the same Wi-Fi network.</span></span>

<span data-ttu-id="7f3e4-257">**執行其他 Spectator 檢視應用程式其他 hololens 時啟動 Spectator 檢視應用程式在行動裝置上的，開啟其攝影機**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-257">**When launching an Spectator View application on a mobile device, other hololens running other Spectator View apps turn on their camera**</span></span>

- <span data-ttu-id="7f3e4-258">Goto NewDeviceDiscovery 元件和變更的廣播金鑰和廣播的連接埠至兩個唯一值。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-258">Goto the NewDeviceDiscovery component and change the both the Broadcast Key and Broadcast port to two unique values.</span></span>
- <span data-ttu-id="7f3e4-259">移至 SpectatorViewDiscovery，並將廣播的索引鍵和廣播的連接埠變更為另一組唯一的數字。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-259">Go to SpectatorViewDiscovery and change the Broadcast Key and Broadcast port to another set of unique numbers.</span></span>

<span data-ttu-id="7f3e4-260">**HoloLens 不會與 mac 的 Unity 編輯器連線。**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-260">**The HoloLens won't connect with the mac Unity Editor.**</span></span>

- <span data-ttu-id="7f3e4-261">這是可以連結它們來 Unity 版本的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-261">This is a known issue which could be linked to the Unity version.</span></span> <span data-ttu-id="7f3e4-262">IPhone 的建置應該仍然運作，並連線正常。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-262">Building to the iPhone should still work and connect as normal.</span></span>

<span data-ttu-id="7f3e4-263">**HoloLens 相機開啟，但無法掃描標記。**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-263">**The HoloLens camera turns on but is not able to scan the marker.**</span></span>

- <span data-ttu-id="7f3e4-264">請確定您建立使用相同的 Unity 編輯器執行個體 （執行之間的不關閉 Unity 建置） 的應用程式的所有版本。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-264">Ensure that you build all versions of the application using the same Unity Editor instance (do not close Unity between builds).</span></span> <span data-ttu-id="7f3e4-265">這是因為未知的問題，使用 Unity。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-265">This is due to an unknown issue with Unity.</span></span>

## <a name="spectator-view-pro"></a><span data-ttu-id="7f3e4-266">Spectator 檢視 Pro</span><span class="sxs-lookup"><span data-stu-id="7f3e4-266">Spectator View Pro</span></span>

![Spectator 檢視安裝程式](images/spectatorview-300px.png)

<span data-ttu-id="7f3e4-268">使用 Pro Spectator 檢視包含以下四個元件：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-268">Using Spectator View Pro involves these four components:</span></span>
1. <span data-ttu-id="7f3e4-269">特別是若要啟用 spectator 檢視，此作業取決於所建置的應用程式[混合實境中共用體驗](shared-experiences-in-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-269">An app built specifically to enable spectator view, which is based on [shared experiences in mixed reality](shared-experiences-in-mixed-reality.md).</span></span>
2. <span data-ttu-id="7f3e4-270">穿著 HoloLens 使用應用程式的使用者。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-270">A user wearing HoloLens using the app.</span></span>
3. <span data-ttu-id="7f3e4-271">提供第三位使用者的觀點來看視訊 spectator 檢視相機 rig。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-271">A spectator view camera rig providing a third-person perspective video.</span></span>
4. <span data-ttu-id="7f3e4-272">桌上型電腦執行分享的經驗的應用程式及複合 （compositing） 全像投影 spectator 檢視影片。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-272">A desktop PC running the shared experience app and compositing the holograms into a spectator view video.</span></span>

![檢視 Pro spectator 的安裝程式](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a><span data-ttu-id="7f3e4-274">使用案例</span><span class="sxs-lookup"><span data-stu-id="7f3e4-274">Use cases</span></span>

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


<span data-ttu-id="7f3e4-275">*Spectator 檢視可用於共用全像攝影版創作，不論它們是靜止影像、 視訊剪輯或即時示範。*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-275">*Spectator view can be used for sharing your holographic creations, whether they're a still image, a video clip, or a live demonstration.*</span></span>


<span data-ttu-id="7f3e4-276">有三個適用於這項技術的重要案例：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-276">There are three key scenarios that work well with this technology:</span></span>

<span data-ttu-id="7f3e4-277">**1.拍攝相片**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-277">**1. Photo capture**</span></span><br>
<span data-ttu-id="7f3e4-278">您可以使用這項技術，來擷取您全像投影的高解析度影像。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-278">Using this technology, you can capture high resolution images of your holograms.</span></span> <span data-ttu-id="7f3e4-279">這些映像可用於展示內容行銷事件、 將傳送給您潛在的用戶端，或甚至是應用程式提交至 Windows 市集。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-279">These images can be used to showcase content at marketing events, send to your potential clients, or even submit your application to the Windows Store.</span></span> <span data-ttu-id="7f3e4-280">您可以決定您想要用來擷取這些映像的相片相機，因此您可能會偏好品質 DSLR 相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-280">You get to decide which photo camera you would like to use to capture these images, as such you may prefer a quality DSLR camera.</span></span>


<span data-ttu-id="7f3e4-281">![檢視 Pro 相片擷取範例 spectator](images/fall-350px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-281">![Spectator View Pro photo capture example](images/fall-350px.jpg)</span></span><br>
<span data-ttu-id="7f3e4-282">*相片擷取範例-讓它顯示下限是由熔岩。*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-282">*Photo capture example - making it appear the floor is made of lava.*</span></span>


<span data-ttu-id="7f3e4-283">**2.影像擷取**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-283">**2. Video capture**</span></span><br>
<span data-ttu-id="7f3e4-284">影片是告訴機制來與許多人共用的全像攝影版的應用程式體驗其最佳意涵。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-284">Videos are the best story telling mechanism for sharing a holographic app experience with many people.</span></span> <span data-ttu-id="7f3e4-285">Spectator 檢視可讓您選擇相機、 功能濾鏡，以及框架最花色您要展示您的應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-285">Spectator view lets you choose the camera, lens, and framing that best suits how you want to showcase your app.</span></span> <span data-ttu-id="7f3e4-286">它可讓您的視訊品質視訊硬體為基礎的控制項中您可以使用。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-286">It puts you in control of the video quality based on the video hardware you have available.</span></span>

<span data-ttu-id="7f3e4-287">![檢視 Pro 視訊擷取範例 spectator](images/spectatorviewvideo.gif)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-287">![Spectator View Pro video capture example](images/spectatorviewvideo.gif)</span></span><br>
<span data-ttu-id="7f3e4-288">*視訊擷取範例-錄製混合的實境共同作業體驗。*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-288">*Video capture example - recording a mixed reality collaboration experience.*</span></span>


<span data-ttu-id="7f3e4-289">**3.實況示範**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-289">**3. Live demonstrations**</span></span><br>
<span data-ttu-id="7f3e4-290">Spectator 檢視是慣用的方法，如即時的示範，因為觀景窗位置會保持穩定或控制。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-290">Spectator view is a preferred approach for live demonstrations as the camera position remains steady or controlled.</span></span> <span data-ttu-id="7f3e4-291">因為您可以使用高品質的視訊攝影機，您也可以產生高品質的影像，適用於大螢幕。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-291">Because you can use a high-quality video camera, you can also produce high-quality images meant for a big screen.</span></span> <span data-ttu-id="7f3e4-292">這也是適用於串流處理實況示範在螢幕上，可能到積極式參與者排隊等候其開啟。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-292">This is also appropriate for streaming live demos on a screen, possibly to eager participants waiting in line for their turn.</span></span>

### <a name="comparing-video-capture-techniques"></a><span data-ttu-id="7f3e4-293">比較視訊擷取技術</span><span class="sxs-lookup"><span data-stu-id="7f3e4-293">Comparing video capture techniques</span></span>

<span data-ttu-id="7f3e4-294">[混合實境擷取](mixed-reality-capture.md)(MRC) 提供的 HoloLens 使用者會看到第一個人點的-檢視從視訊的複合。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-294">[Mixed reality capture](mixed-reality-capture.md) (MRC) provides a video composite of what the HoloLens user is seeing from a first person point-of-view.</span></span> <span data-ttu-id="7f3e4-295">Spectator 檢視產生的第三位使用者的觀點而言，可讓視訊的觀察者，以查看具有全像投影和穿著 HoloLens 裝置的使用者環境的影片。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-295">Spectator view produces a video from a third-person perspective, allowing the video observer to see the environment with holograms and the user wearing a HoloLens device.</span></span> <span data-ttu-id="7f3e4-296">因為您必須選擇一種數位相機，spectator 檢視也可以產生較高的解析度和更佳的品質影像，比 MRC 映像所使用的內建 HoloLens 相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-296">Because you have a choice of camera, spectator views can also produce higher resolution and better quality images than the built-in HoloLens camera used for MRC images.</span></span> <span data-ttu-id="7f3e4-297">基於這個理由，spectator 檢視比較適合大型應用程式映像，在 Windows 市集中，行銷的影片，或對象為投影的即時檢視。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-297">For this reason, spectator view is better suited for app images in the Windows Store, marketing videos, or for projecting a live view for an audience.</span></span>

<span data-ttu-id="7f3e4-298">![檢視 Pro spectator Microsoft 重點演說簡報中使用專業相機](images/spectator-view-professional-red-camera-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-298">![Spectator View Pro professional camera used in Microsoft keynote presentations](images/spectator-view-professional-red-camera-300px.jpg)</span></span><br>
<span data-ttu-id="7f3e4-299">*檢視 Pro spectator Microsoft 重點演說簡報中使用專業相機*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-299">*Spectator View Pro professional camera used in Microsoft keynote presentations*</span></span>


<span data-ttu-id="7f3e4-300">Spectator 檢視已經過 Microsoft HoloLens 已呈現方式體驗的對象自一開始在 2015 年 1 月發表產品時的必要部分。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-300">Spectator view has been an essential piece of how Microsoft HoloLens has presented experiences to audiences since the very beginning when the product was announced in January 2015.</span></span> <span data-ttu-id="7f3e4-301">使用專業的安裝程式會有高需求和昂貴的價格標記，請為它。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-301">The professional setup used had high demands and an expensive price tag to go with it.</span></span> <span data-ttu-id="7f3e4-302">比方說，相機會使用 genlock 訊號，以確保會追蹤系統 HoloLens 與協調的確切時間。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-302">For example, the camera uses a genlock signal to ensure precise timing that coordinates with the HoloLens tracking system.</span></span> <span data-ttu-id="7f3e4-303">在此設定中，移動 spectator 檢視相機無法同時全像投影穩定符合所查看的內容直接在 HoloLens 經驗的人的體驗。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-303">In this setup, moving the spectator view camera was possible while keeping holograms stable to match the experience of someone who is seeing the experience directly in HoloLens.</span></span>

<span data-ttu-id="7f3e4-304">移動相機 rig，以大幅降低整體安裝程式的成本的功能時，需 spectator 檢視的開放原始碼版本。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-304">The open-source version of spectator view trades off the ability to move the camera rig in order to dramatically lower the cost of the overall setup.</span></span> <span data-ttu-id="7f3e4-305">此專案會使用嚴格掛接到 HoloLens 外部相機邴畫觶圖片和影片的全像攝影版的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-305">This project uses an external camera rigidly mounted to a HoloLens to take high-definition pictures and video of your holographic Unity project.</span></span> <span data-ttu-id="7f3e4-306">**在即時的示範期間相機應維持固定位置。**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-306">**During live demonstrations, the camera should remain in a fixed position.**</span></span> <span data-ttu-id="7f3e4-307">觀景窗移動可能會導致闀抖動或漂移。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-307">Movement of the camera can lead to hologram jitter or drift.</span></span> <span data-ttu-id="7f3e4-308">這是因為視訊畫面格的時間和全像投影在電腦上的呈現可能不會精確地同步處理。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-308">This is because the timing of the video frame and the rendering of holograms on the PC may not be precisely synchronized.</span></span> <span data-ttu-id="7f3e4-309">因此，讓觀景窗保持穩定或限制移動會產生接近穿著 HoloLens 的人員可以看到結果。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-309">Therefore, keeping the camera steady or limiting movement will produce a result close to what the person wearing a HoloLens can see.</span></span>

<span data-ttu-id="7f3e4-310">若要讓您的應用程式準備好 spectator 檢視，您必須建置[共用體驗](holograms-240.md)應用程式，並確保應用程式可以執行 HoloLens 以及在 Unity 編輯器中的桌面。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-310">To make your app ready for spectator view, you'll need to build a [shared experience](holograms-240.md) app and ensure the app can run on both HoloLens as well as desktop in the Unity editor.</span></span> <span data-ttu-id="7f3e4-311">桌面版本的應用程式必須在該複合視訊摘要與呈現全像投影中建置的其他元件。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-311">The desktop version of the app will have additional components built in that composite the video feed with the rendered holograms.</span></span>

## <a name="how-to-set-up-spectator-view-pro"></a><span data-ttu-id="7f3e4-312">如何設定 Pro Spectator 檢視</span><span class="sxs-lookup"><span data-stu-id="7f3e4-312">How to set up Spectator View Pro</span></span> 

### <a name="requirements"></a><span data-ttu-id="7f3e4-313">需求</span><span class="sxs-lookup"><span data-stu-id="7f3e4-313">Requirements</span></span>

![Spectator 檢視 Pro Rig](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a><span data-ttu-id="7f3e4-315">硬體購物清單</span><span class="sxs-lookup"><span data-stu-id="7f3e4-315">Hardware shopping list</span></span>

<span data-ttu-id="7f3e4-316">以下是建議的硬體清單，但您可以也試驗其他相容的單位。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-316">Below is a recommended list of hardware, but you can experiment with other compatible units too.</span></span> 

|<span data-ttu-id="7f3e4-317">硬體元件</span><span class="sxs-lookup"><span data-stu-id="7f3e4-317">Hardware component</span></span>                                                                     |<span data-ttu-id="7f3e4-318">建議</span><span class="sxs-lookup"><span data-stu-id="7f3e4-318">Recommendation</span></span>               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|<span data-ttu-id="7f3e4-319">適用於使用 HoloLens 模擬器的全像攝影版開發的電腦設定</span><span class="sxs-lookup"><span data-stu-id="7f3e4-319">A PC configuration that works for holographic development with the HoloLens emulator</span></span>  |                              | 
|<span data-ttu-id="7f3e4-320">相機與 out HDMI 或拍攝相片 SDK</span><span class="sxs-lookup"><span data-stu-id="7f3e4-320">Camera with HDMI out or photo capture SDK</span></span>                                             | <span data-ttu-id="7f3e4-321">如需相片和視訊擷取，我們已測試過[還要 EOS 5d Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-321">For photo and video capture, we have tested the [Canon EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) camera.</span></span> <span data-ttu-id="7f3e4-322">針對即時的示範，我們已測試過[Blackmagic 設計生產相機 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-322">For live demonstrations, we have tested the [Blackmagic Design Production Camera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).</span></span><br><br><span data-ttu-id="7f3e4-323">請注意，普通的相機具有 HDMI 出 (例如 GoPro) 應該會運作。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-323">Note, any camera with HDMI out (e.g. GoPro) should work.</span></span> <span data-ttu-id="7f3e4-324">許多我們的影片使用[Canon EF 14 mm f/2.8 L II USM Ultra-wide 角度固定功能濾鏡](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)，但您應該選擇相機功能濾鏡，符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-324">Many of our videos use the [Canon EF 14mm f/2.8L II USM Ultra-Wide Angle Fixed Lens](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), but you should choose a camera lens that meets your needs.</span></span> | 
|<span data-ttu-id="7f3e4-325">擷取您的電腦，以取得從您的相機校正 rig 並預覽您的複合場景的色彩框架的卡片</span><span class="sxs-lookup"><span data-stu-id="7f3e4-325">Capture card for your PC to get color frames from your camera to calibrate your rig and preview your composite scene</span></span> |  <span data-ttu-id="7f3e4-326">我們已測試過[Blackmagic 設計濃度 4k 擷取 pro](https://www.amazon.com/dp/B00U3QNP7Q)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-326">We have tested the [Blackmagic Design Intensity Pro 4K capture card](https://www.amazon.com/dp/B00U3QNP7Q).</span></span> | 
|<span data-ttu-id="7f3e4-327">纜線</span><span class="sxs-lookup"><span data-stu-id="7f3e4-327">Cables</span></span>                                                                                 |  <span data-ttu-id="7f3e4-328">[以迷你 HDMI HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)提供將相機連接至您擷取卡。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-328">[HDMI to Mini HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) for attaching your camera to your capture card.</span></span> <span data-ttu-id="7f3e4-329">請確定您購買符合您的相機 HDMI 外型規格。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-329">Ensure you purchase an HDMI form factor that fits your camera.</span></span> <span data-ttu-id="7f3e4-330">(GoPro，比方說，將輸出透過[Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1)。)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-330">(GoPro, for instance, outputs over [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)</span></span><br><br><span data-ttu-id="7f3e4-331">[HDMI 纜線](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)檢視複合預覽監視器或電視上的摘要</span><span class="sxs-lookup"><span data-stu-id="7f3e4-331">[HDMI cable](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) for viewing the composite feed on a preview monitor or television</span></span> | 
|<span data-ttu-id="7f3e4-332">台到您的 HoloLens 攝影機 aluminum 括號。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-332">Machined aluminum bracket to connect your HoloLens to the camera.</span></span> | [<span data-ttu-id="7f3e4-333">Aluminum 括號</span><span class="sxs-lookup"><span data-stu-id="7f3e4-333">Aluminum bracket</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|<span data-ttu-id="7f3e4-334">3D 列印與數位相機 hotshoe HoloLens 掛接的配接器。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-334">3D printed adapter to connect the HoloLens mount to the camera hotshoe.</span></span>| [<span data-ttu-id="7f3e4-335">3D 列印的配接器</span><span class="sxs-lookup"><span data-stu-id="7f3e4-335">3D printed adapter</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|<span data-ttu-id="7f3e4-336">若要掛接 hotshoe 配接器的 Hotshoe fastener</span><span class="sxs-lookup"><span data-stu-id="7f3e4-336">Hotshoe fastener to mount the hotshoe adapter</span></span>                                       |  [<span data-ttu-id="7f3e4-337">Hotshoe Fastener</span><span class="sxs-lookup"><span data-stu-id="7f3e4-337">Hotshoe Fastener</span></span>](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|<span data-ttu-id="7f3e4-338">各種的資訊、 bolt 和工具</span><span class="sxs-lookup"><span data-stu-id="7f3e4-338">Assorted nuts, bolts, and tools</span></span>                                                |  [<span data-ttu-id="7f3e4-339">1/4 到 20 」 資訊</span><span class="sxs-lookup"><span data-stu-id="7f3e4-339">1/4-20" Nuts</span></span>](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[<span data-ttu-id="7f3e4-340">1/4-20"x 3/4 」 Bolt</span><span class="sxs-lookup"><span data-stu-id="7f3e4-340">1/4-20" x 3/4" Bolts</span></span>](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[<span data-ttu-id="7f3e4-341">7/16 糖堅果驅動程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-341">7/16 Nut Driver</span></span>](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[<span data-ttu-id="7f3e4-342">T15 Torx</span><span class="sxs-lookup"><span data-stu-id="7f3e4-342">T15 Torx</span></span>](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[<span data-ttu-id="7f3e4-343">T7 Torx</span><span class="sxs-lookup"><span data-stu-id="7f3e4-343">T7 Torx</span></span>](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a><span data-ttu-id="7f3e4-344">軟體元件</span><span class="sxs-lookup"><span data-stu-id="7f3e4-344">Software components</span></span>

1. <span data-ttu-id="7f3e4-345">從下載軟體[spectator 檢視的 GitHub 專案](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-345">Software downloaded from the [GitHub project for spectator view](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).</span></span>
2. <span data-ttu-id="7f3e4-346">[Blackmagic 擷取卡 SDK](https://www.blackmagicdesign.com/support)。 \\</span><span class="sxs-lookup"><span data-stu-id="7f3e4-346">[Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="7f3e4-347">桌面的視訊開發人員 SDK 中 「 最新的下載 」 搜尋。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-347">Search for Desktop Video Developer SDK in "Latest Downloads".</span></span>
3. <span data-ttu-id="7f3e4-348">[Blackmagic 桌面視訊的執行階段](https://www.blackmagicdesign.com/support)。 \\</span><span class="sxs-lookup"><span data-stu-id="7f3e4-348">[Blackmagic Desktop Video Runtime](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="7f3e4-349">在 最新版本下載 「 桌面的視訊軟體更新的搜尋。 \\</span><span class="sxs-lookup"><span data-stu-id="7f3e4-349">Search for Desktop Video Software Update in "Latest Downloads".\\</span></span>
 <span data-ttu-id="7f3e4-350">請確定版本編號相符的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-350">Ensure the version number matches the SDK version.</span></span>
4. <span data-ttu-id="7f3e4-351">[OpenCV 3.1](https://opencv.org/releases.html)校正或視訊擷取，而不需要 Blackmagic 擷取卡。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-351">[OpenCV 3.1](https://opencv.org/releases.html) For calibration or video capture without the Blackmagic capture card.</span></span>
5. <span data-ttu-id="7f3e4-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) （選擇性）。 \\</span><span class="sxs-lookup"><span data-stu-id="7f3e4-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional).\\</span></span>
 <span data-ttu-id="7f3e4-353">如果您使用 Canon 相機，並享有 Canon SDK，您可以 tether 至您的電腦，才會更高解析度影像的相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-353">If you are using a Canon camera and have access to the Canon SDK, you can tether your camera to your PC to take higher resolution images.</span></span>
6. <span data-ttu-id="7f3e4-354">Unity 的全像攝影版的應用程式開發。 \\</span><span class="sxs-lookup"><span data-stu-id="7f3e4-354">Unity for your holographic app development.\\</span></span>
 <span data-ttu-id="7f3e4-355">OSS 專案中，可以找到支援的版本。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-355">Supported version can be found in the OSS project.</span></span>
7. <span data-ttu-id="7f3e4-356">具有最新更新的 visual Studio 2015。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-356">Visual Studio 2015 with latest updates.</span></span>

### <a name="building-your-own-spectator-view-pro-camera"></a><span data-ttu-id="7f3e4-357">建置您自己 Spectator 檢視 Pro 相機</span><span class="sxs-lookup"><span data-stu-id="7f3e4-357">Building your own Spectator View Pro camera</span></span>

<span data-ttu-id="7f3e4-358">**請注意 &AMP; 免責聲明：** 在修改 HoloLens 硬體 （包括但不是限於，設定 「 spectator 檢視 」 您 HoloLens） 基本時，應該一律要觀察安全性預防措施。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-358">**NOTICE & DISCLAIMER:** When making modifications to your HoloLens hardware (including, but not limited to, setting up your HoloLens for "spectator view") basic safety precautions should always be observed.</span></span> <span data-ttu-id="7f3e4-359">進行任何修改之前，先閱讀所有指示與手冊。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-359">Read all instructions and manuals before making any modifications.</span></span> <span data-ttu-id="7f3e4-360">您必須負責遵循所有的指示，並使用工具的指示。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-360">It is your responsibility to follow all instructions and use tools as directed.</span></span> <span data-ttu-id="7f3e4-361">您可能已購買或授權您 HoloLens 與有限瑕疵責任擔保 」 或 「 不提供任何擔保。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-361">You may have purchased or licensed your HoloLens with a limited warranty or no warranty.</span></span> <span data-ttu-id="7f3e4-362">請先閱讀您適用[HoloLens 授權合約或使用規定及銷售](https://www.microsoft.com/hololens/support/warranty)若要了解您擔保的選項。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-362">Please read your applicable [HoloLens License Agreement or Terms of Use and Sale](https://www.microsoft.com/hololens/support/warranty) to understand your warranty options.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a><span data-ttu-id="7f3e4-363">Rig 組件</span><span class="sxs-lookup"><span data-stu-id="7f3e4-363">Rig Assembly</span></span>

<span data-ttu-id="7f3e4-364">![HoloLens 和 DSLR 相機的組合的 Spectator 檢視 Pro rig。](images/assembly.gif)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-364">![Assembled Spectator View Pro rig with HoloLens and DSLR camera.](images/assembly.gif)</span></span><br>
<span data-ttu-id="7f3e4-365">*組裝的 Spectator 檢視專業人員的 rig HoloLens 和 DSLR 相機*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-365">*Assembled Spectator View Pro rig with HoloLens and DSLR camera*</span></span>


* <span data-ttu-id="7f3e4-366">若要移除的 HoloLens 髮帶使用 T7 螺絲起子。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-366">Use a T7 screwdriver to remove the headband from the HoloLens.</span></span> <span data-ttu-id="7f3e4-367">鬆散的螺絲之後，請加上來自另一端迴紋針逛方式。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-367">Once the screws are loose, poke them out with a paperclip from the other side.</span></span>
* <span data-ttu-id="7f3e4-368">移除螺絲上限，在內部使用小型的一般標頭螺絲起子 HoloLens 上面的前端。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-368">Remove the screw cap on the inside front of the HoloLens visor with a small flat head screwdriver.</span></span>
* <span data-ttu-id="7f3e4-369">若要移除的 HoloLens 括號，若要移除您的小型 torx bolt 使用 T15 螺絲起子和攔截形狀的附件。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-369">Use a T15 screwdriver to remove the small torx bolts from the HoloLens bracket to remove the U and Hook-shaped attachments.</span></span>
* <span data-ttu-id="7f3e4-370">置於括號，上面的內側上使用方括號前面立體化公開孔對齊 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-370">Place the HoloLens on the bracket, lining up the exposed hole on the inside of the visor with the extrusion on the front of the bracket.</span></span> <span data-ttu-id="7f3e4-371">HoloLens' 手臂應該保留的方括號下方 pin。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-371">The HoloLens' arms should be kept in place by the pins on the bottom of the bracket.</span></span>
* <span data-ttu-id="7f3e4-372">將您重新附加和攔截形狀來保護以方括號 HoloLens 的附件。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-372">Reattach the U and Hook-shaped attachments to secure the HoloLens to the bracket.</span></span>
* <span data-ttu-id="7f3e4-373">將 hotshoe fastener 附加至您的相機的 hotshoe 中。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-373">Attach the hotshoe fastener to the hotshoe of your camera.</span></span>
* <span data-ttu-id="7f3e4-374">將裝載配接器連接至 hotshoe fastener 中。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-374">Attach the mount adapter to the hotshoe fastener.</span></span>
* <span data-ttu-id="7f3e4-375">旋轉相機功能濾鏡的平行與配接器讓朝窄的側邊。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-375">Rotate the adapter so the narrow side is facing forward and parallel to the camera's lens.</span></span>
* <span data-ttu-id="7f3e4-376">使用 7/16 糖堅果驅動程式 1/4 」 糖堅果與安全位置中的配接器。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-376">Secure the adapter in place with a 1/4" nut using the 7/16 nut driver.</span></span>
* <span data-ttu-id="7f3e4-377">因此 HoloLens' 上面的前面是盡可能接近相機功能濾鏡的最上層的位置對配接器的括號。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-377">Position the bracket against the adapter so the front of the HoloLens' visor is as close as possible to the front of the camera's lens.</span></span>
* <span data-ttu-id="7f3e4-378">4 1/4 」 具體細節使用 7/16 糖堅果驅動程式與附加括號。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-378">Attach the bracket with 4 1/4" nuts and bolts using the 7/16 nut driver.</span></span>

#### <a name="pc-setup"></a><span data-ttu-id="7f3e4-379">電腦安裝程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-379">PC Setup</span></span>
* <span data-ttu-id="7f3e4-380">從 [軟體元件] 區段中安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-380">Install the software from the software components section.</span></span>
* <span data-ttu-id="7f3e4-381">加入在主機板上開啟 PCIe 位置擷取卡。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-381">Add the capture card to an open PCIe slot on your motherboard.</span></span>
* <span data-ttu-id="7f3e4-382">從相機到外部 HDMI 位置 HDMI 纜線 （HDMI 單元） 擷取卡。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-382">Plug an HDMI cable from your camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>
* <span data-ttu-id="7f3e4-383">插入從中心 HDMI 插槽 （HDMI 外） 擷取卡選擇性預覽監視器 HDMI 纜線。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-383">Plug an HDMI cable from the center HDMI slot (HDMI-Out) on the capture card to an optional preview monitor.</span></span>

#### <a name="camera-setup"></a><span data-ttu-id="7f3e4-384">照相機設定</span><span class="sxs-lookup"><span data-stu-id="7f3e4-384">Camera Setup</span></span>
* <span data-ttu-id="7f3e4-385">因此它會輸出在完整解析度 1920 x 1080、jpeg 而不裁剪 3:4 相片的解析度，則您可以將視訊模式相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-385">Change your camera to Video Mode so it outputs at the full 1920x1080 resolution rather than a cropped 3:4 photo resolution.</span></span>
* <span data-ttu-id="7f3e4-386">尋找您的相機 HDMI 設定並啟用**鏡像**或是**雙重監視器**。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-386">Find your camera's HDMI settings and enable **Mirroring** or **Dual Monitor**.</span></span>
* <span data-ttu-id="7f3e4-387">設定輸出解析度 1080 p</span><span class="sxs-lookup"><span data-stu-id="7f3e4-387">Set the output resolution to 1080P.</span></span>
* <span data-ttu-id="7f3e4-388">關閉**即時檢視在螢幕上顯示**讓複合摘要中看不到任何螢幕覆疊。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-388">Turn off **Live View On Screen Display** so any screen overlays do not appear in the composite feed.</span></span>
* <span data-ttu-id="7f3e4-389">開啟您的相機**即時檢視**。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-389">Turn on your camera's **Live View**.</span></span>
* <span data-ttu-id="7f3e4-390">如果使用**Canon SDK**而且想要使用 flash 單位，請停用**無訊息 LV 限定**。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-390">If using the **Canon SDK** and would like to use a flash unit, disable **Silent LV Shoot**.</span></span>
* <span data-ttu-id="7f3e4-391">從相機到外部 HDMI 位置 HDMI 纜線 （HDMI 單元） 擷取卡。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-391">Plug an HDMI cable from the camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>

#### <a name="calibration"></a><span data-ttu-id="7f3e4-392">校正</span><span class="sxs-lookup"><span data-stu-id="7f3e4-392">Calibration</span></span>

<span data-ttu-id="7f3e4-393">設定好您的觀眾檢視 rig 之後，您必須校正以取得您 HoloLens 相機的位置和旋轉位移。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-393">After setting up your spectator view rig, you must calibrate in order to get the position and rotation offset of your camera to your HoloLens.</span></span>
* <span data-ttu-id="7f3e4-394">開啟下 Calibration\Calibration.sln 校正 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-394">Open the Calibration Visual Studio solution under Calibration\Calibration.sln.</span></span>
* <span data-ttu-id="7f3e4-395">在此解決方案中，您會發現檔案 dependencies.props 這會建立內含位置的第 3 個合作對象來源的巨集。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-395">In this solution, you will find the file dependencies.props which creates macros for the inc locations of the 3rd party sources.</span></span>
* <span data-ttu-id="7f3e4-396">更新這個檔案的位置您安裝 OpenCV 3.1、 Blackmagic SDK 和 Canon SDK （如果適用）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-396">Update this file with the location you installed OpenCV 3.1, the Blackmagic SDK, and the Canon SDK (if applicable)</span></span>

<span data-ttu-id="7f3e4-397">![Visual Studio 中的相依性位置快照集](images/dependencies-600px.png)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-397">![Dependency locations snapshot in Visual Studio](images/dependencies-600px.png)</span></span><br>
<span data-ttu-id="7f3e4-398">*Visual Studio 中的相依性位置快照集*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-398">*Dependency locations snapshot in Visual Studio*</span></span>


* <span data-ttu-id="7f3e4-399">印出校正模式 Calibration\CalibrationPatterns\2_66_grid_FULL.png 一般、 固定介面上。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-399">Print out the calibration pattern Calibration\CalibrationPatterns\2_66_grid_FULL.png on a flat, rigid surface.</span></span>
* <span data-ttu-id="7f3e4-400">透過 USB 插入您的電腦程式 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-400">Plug your HoloLens into your PC over USB.</span></span>
* <span data-ttu-id="7f3e4-401">更新的前置處理器定義**HOLOLENS_USER**並**HOLOLENS_PW**中**stdafx.h**有 HoloLens' 裝置入口網站的認證。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-401">Update the preprocessor definitions **HOLOLENS_USER** and **HOLOLENS_PW** in **stdafx.h** with your HoloLens' device portal credentials.</span></span>
* <span data-ttu-id="7f3e4-402">HDMI 移轉時，將相機連接至擷取卡，並將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-402">Attach your camera to your capture card over HDMI and turn it on.</span></span>
* <span data-ttu-id="7f3e4-403">執行校正解決方案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-403">Run the Calibration solution.</span></span>
* <span data-ttu-id="7f3e4-404">移動棋盤式圖樣周圍的檢視，像這樣：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-404">Move the checkerboard pattern around the view like this:</span></span>

<span data-ttu-id="7f3e4-405">![校正 Spectator 檢視 Pro rig](images/calibration.gif)</span><span class="sxs-lookup"><span data-stu-id="7f3e4-405">![Calibrating the Spectator View Pro rig](images/calibration.gif)</span></span><br>
<span data-ttu-id="7f3e4-406">*校正 Spectator 檢視 Pro rig*</span><span class="sxs-lookup"><span data-stu-id="7f3e4-406">*Calibrating the Spectator View Pro rig*</span></span>


* <span data-ttu-id="7f3e4-407">棋盤式檢視中時，會自動採取一張圖片。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-407">A picture will automatically be taken when a checkerboard is in view.</span></span> <span data-ttu-id="7f3e4-408">移至下一步 的姿勢之前尋找 HoloLens' 上面白色燈。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-408">Look for the white light on the HoloLens' visor before advancing to the next pose.</span></span>
* <span data-ttu-id="7f3e4-409">完成時，按下**Enter**校正應用程式在建立焦點**CalibrationData.txt**檔案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-409">When finished, press **Enter** with the Calibration app in focus to create a **CalibrationData.txt** file.</span></span>
* <span data-ttu-id="7f3e4-410">此檔案會儲存至**Documents\CalibrationFiles\CalibrationData.txt**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-410">This file will be saved to **Documents\CalibrationFiles\CalibrationData.txt**</span></span>
* <span data-ttu-id="7f3e4-411">檢查這個檔案來查看您校正資料是否正確：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-411">Inspect this file to see if your calibration data is accurate:</span></span>
   * <span data-ttu-id="7f3e4-412">**DSLR RMS**應該接近 0。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-412">**DSLR RMS** should be close to 0.</span></span>
   * <span data-ttu-id="7f3e4-413">**HoloLens RMS**應該接近 0。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-413">**HoloLens RMS** should be close to 0.</span></span>
   * <span data-ttu-id="7f3e4-414">**立體聲 RMS**可能是 20-50，這是可接受因為之間兩個相機的視野，可能會不同。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-414">**Stereo RMS** may be 20-50, this is acceptable since the field of view between the two cameras may be different.</span></span>
   * <span data-ttu-id="7f3e4-415">**轉譯**是 HoloLens' 相機中要附加的相機功能濾鏡的距離。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-415">**Translation** is the distance from the HoloLens' camera to the attached camera's lens.</span></span> <span data-ttu-id="7f3e4-416">這是以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-416">This is in meters.</span></span>
   * <span data-ttu-id="7f3e4-417">**旋轉**應該接近身分識別。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-417">**Rotation** should be close to identity.</span></span>
   * <span data-ttu-id="7f3e4-418">**DSLR_fov** y 值應該接近垂直檢視欄位必須是從功能濾鏡的焦距和任何相機主體裁剪因素。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-418">**DSLR_fov** y value should be close to the vertical field of view expected from your lens' focal length and any camera body crop factor.</span></span>
* <span data-ttu-id="7f3e4-419">如果任何上述的值似乎沒有意義，校準。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-419">If any of the above values do not appear to make sense, recalibrate.</span></span>
* <span data-ttu-id="7f3e4-420">這個檔案複製到**資產**目錄中您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-420">Copy this file to the **Assets** directory in your Unity project.</span></span>

### <a name="compositor"></a><span data-ttu-id="7f3e4-421">撰寫器</span><span class="sxs-lookup"><span data-stu-id="7f3e4-421">Compositor</span></span>

<span data-ttu-id="7f3e4-422">複合項是以在 Unity 編輯器視窗中執行的 Unity 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-422">The compositor is a Unity extension that runs as a window in the Unity editor.</span></span> <span data-ttu-id="7f3e4-423">若要啟用此功能，複合項 Visual Studio 方案必須先建置。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-423">To enable this, the Compositor Visual Studio solution first needs to be built.</span></span>
* <span data-ttu-id="7f3e4-424">開啟下 Compositor\Compositor.sln 複合項 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="7f3e4-424">Open the Compositor Visual Studio solution under Compositor\Compositor.sln</span></span>
* <span data-ttu-id="7f3e4-425">更新 dependencies.props 校正解決方案上述的相同準則。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-425">Update dependencies.props with the same criteria from the Calibration solution above.</span></span> <span data-ttu-id="7f3e4-426">如果您遵循校正步驟時，此檔案會有已更新。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-426">If you followed the calibration steps, this file will already have been updated.</span></span>
* <span data-ttu-id="7f3e4-427">建置整個解決方案，做為版本和架構符合您的 Unity 版本的架構。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-427">Build the entire solution as Release and the architecture that matches your Unity version's architecture.</span></span> <span data-ttu-id="7f3e4-428">如果在有疑問，建置 x86 和 x64。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-428">If in doubt, build both x86 and x64.</span></span>
* <span data-ttu-id="7f3e4-429">如果您建置適用於 x64 的解決方案，也建置 SpatialPerceptionHelper 專案為 x86，因為它會執行 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-429">If you built the solution for x64, also build the SpatialPerceptionHelper project as x86 since it will run on the HoloLens.</span></span>
* <span data-ttu-id="7f3e4-430">如果執行您的應用程式，請關閉 Unity。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-430">Close Unity if it is running your application.</span></span> <span data-ttu-id="7f3e4-431">Unity 必須 Dll 會在執行階段變更如果會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-431">Unity needs to be relaunched if DLLs are changed at runtime.</span></span>
* <span data-ttu-id="7f3e4-432">執行 Compositor\CopyDLL.cmd 複製到 Unity 專案從這個方案所建置的 Dll。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-432">Run Compositor\CopyDLL.cmd to copy the DLLs built from this solution to your Unity project.</span></span> <span data-ttu-id="7f3e4-433">此指令碼會將 Dll 複製至包含的範例專案中。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-433">This script will copy the DLLs to the included sample project.</span></span> <span data-ttu-id="7f3e4-434">設定您自己的專案之後，您可以執行 CopyDLL 以指向您的專案資產目錄，也那里複製的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-434">Once you have your own project set up, you can run CopyDLL with a command line argument pointing to your project's Assets directory to copy there as well.</span></span>
* <span data-ttu-id="7f3e4-435">啟動範例 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-435">Launch the sample Unity app.</span></span>

### <a name="unity-app"></a><span data-ttu-id="7f3e4-436">Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="7f3e4-436">Unity app</span></span>

<span data-ttu-id="7f3e4-437">複合項會執行在 Unity 編輯器的視窗。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-437">The compositor runs as a window in the Unity Editor.</span></span> <span data-ttu-id="7f3e4-438">包含的範例專案會有所有項目設定為使用 spectator 檢視一次複製 Dll 的複合。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-438">The included sample project has everything set up to work with spectator view once the compositor DLLs are copied.</span></span>

<span data-ttu-id="7f3e4-439">Spectator 檢視需要應用程式做為執行[共用體驗](holograms-240.md)。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-439">Spectator view requires the application to be run as a [shared experience](holograms-240.md).</span></span> <span data-ttu-id="7f3e4-440">這表示 HoloLens 上發生的任何應用程式狀態變更需要更新過在 Unity 中執行的應用程式之間的網路。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-440">This means that any application state changes that happen on the HoloLens need to be networked to update the app running in Unity too.</span></span>

<span data-ttu-id="7f3e4-441">如果新的 Unity 專案從開始，您必須先進行一些設定：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-441">If starting from a new Unity project, you will need to do some setup first:</span></span>
* <span data-ttu-id="7f3e4-442">複製**資產/附加元件/HolographicCameraRig**範例專案到您的專案。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-442">Copy **Assets/Addons/HolographicCameraRig** from the sample project to your project.</span></span>
* <span data-ttu-id="7f3e4-443">將最新的 MixedRealityToolkit 新增至您的專案，包括**Sharing**， **csc.rsp**， **gmcs.rsp**，以及**smcs.rsp**。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-443">Add the latest MixedRealityToolkit to your project, including **Sharing**, **csc.rsp**, **gmcs.rsp**, and **smcs.rsp**.</span></span>
* <span data-ttu-id="7f3e4-444">新增您**CalibrationData.txt**檔案至您的資產目錄。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-444">Add your **CalibrationData.txt** file to your Assets directory.</span></span>

![Unity 資產目錄快照集](images/files-400px.png)

* <span data-ttu-id="7f3e4-446">新增**HolographicCameraRig\Prefabs\SpectatorViewManager** prefab 至場景並填寫各欄位：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-446">Add the **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab to your scene and fill in the fields:</span></span>
   * <span data-ttu-id="7f3e4-447">**HolographicCameraManager**應該填入從 HolographicCameraRig prefab 目錄 HolographicCameraManager prefab。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-447">**HolographicCameraManager** should be populated with the HolographicCameraManager prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="7f3e4-448">**錨點**應該填入從 HolographicCameraRig prefab 目錄錨點 prefab。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-448">**Anchor** should be populated with the Anchor prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="7f3e4-449">**共用**應該填入從 MixedRealityToolkit 共用 prefab。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-449">**Sharing** should be populated with the Sharing prefab from the MixedRealityToolkit.</span></span>
   * <span data-ttu-id="7f3e4-450">注意：如果任何這些 prefabs 已存在於您的專案階層架構中，將使用現有 prefabs，而不是下列項目。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-450">Note: If any of these prefabs already exist in your project hierarchy, the existing prefabs will be used instead of these ones.</span></span>
   * <span data-ttu-id="7f3e4-451">**Spectator 檢視 IP**應該附加至您的觀眾檢視 rig 您 HoloLens 的 IP。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-451">**Spectator View IP** should be the IP of your HoloLens attached to your spectator view rig.</span></span>
   * <span data-ttu-id="7f3e4-452">**共用服務 IP**應該執行 MixedRealityToolkit SharingService 電腦的 IP。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-452">**Sharing Service IP** should be the IP of the PC running the MixedRealityToolkit SharingService.</span></span>
   * <span data-ttu-id="7f3e4-453">選擇性：如果您有多個檢視附加至多個電腦的 rig 的 spectator 的**本機電腦 IP**應該設有 spectator 檢視 rig 會與通訊的電腦。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-453">Optional: If you have multiple spectator view rigs attached to multiple PC's, **Local Computer IP** should be set with the PC the spectator view rig will communicate with.</span></span>

![在 Unity 中的 spectator 檢視管理員屬性](images/spectatorviewmanager-500px.png)

* <span data-ttu-id="7f3e4-455">啟動 MixedRealityToolkit**共用服務**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-455">Start the MixedRealityToolkit **Sharing Service**</span></span>
* <span data-ttu-id="7f3e4-456">建置及部署應用程式，以 HoloLens D3D UWP 連接至 spectator 檢視 rig。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-456">Build and deploy the app as a D3D UWP to the HoloLens attached to the spectator view rig.</span></span>
* <span data-ttu-id="7f3e4-457">將應用程式部署到體驗中的任何其他 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-457">Deploy the app to any other HoloLens devices in the experience.</span></span>
* <span data-ttu-id="7f3e4-458">請檢查**在背景中執行**下方的核取方塊**編輯/專案設定/播放程式**。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-458">Check the **Run In Background** checkbox under **edit/project settings/player**.</span></span>

![在 Unity 中的背景設定中執行](images/run-in-bg-400px.png)
* <span data-ttu-id="7f3e4-460">啟動 [複合] 視窗下的**Spectator 檢視複合項**</span><span class="sxs-lookup"><span data-stu-id="7f3e4-460">Launch the compositor window under **Spectator View/Compositor**</span></span>

![在 Unity 中的 [spectator] 檢視的複合檢視](images/compositor-500px.png)

* <span data-ttu-id="7f3e4-462">此視窗可讓您：</span><span class="sxs-lookup"><span data-stu-id="7f3e4-462">This window allows you to:</span></span>
   * <span data-ttu-id="7f3e4-463">開始錄製影片</span><span class="sxs-lookup"><span data-stu-id="7f3e4-463">Start recording video</span></span>
   * <span data-ttu-id="7f3e4-464">拍照</span><span class="sxs-lookup"><span data-stu-id="7f3e4-464">Take a picture</span></span>
   * <span data-ttu-id="7f3e4-465">變更全像圖不透明度</span><span class="sxs-lookup"><span data-stu-id="7f3e4-465">Change hologram opacity</span></span>
   * <span data-ttu-id="7f3e4-466">變更框架位移 （以調整色彩時間戳記的擷取卡片的延遲）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-466">Change the frame offset (which adjusts the color timestamp to account for capture card latency)</span></span>
   * <span data-ttu-id="7f3e4-467">開啟要儲存擷取的目錄</span><span class="sxs-lookup"><span data-stu-id="7f3e4-467">Open the directory the captures are saved to</span></span>
   * <span data-ttu-id="7f3e4-468">要求 spectator 檢視相機中的空間的對應資料 （如果 SpatialMappingManager 存在於您的專案）</span><span class="sxs-lookup"><span data-stu-id="7f3e4-468">Request spatial mapping data from the spectator view camera (if a SpatialMappingManager exists in your project)</span></span>
   * <span data-ttu-id="7f3e4-469">個別視覺化場景的複合檢視，以及色彩、 全像投影和 alpha 色頻。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-469">Visualize the scene's composite view as well as color, holograms, and alpha channel individually.</span></span>
   * <span data-ttu-id="7f3e4-470">開啟您的相機。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-470">Turn your camera on.</span></span>
   * <span data-ttu-id="7f3e4-471">在 Unity 中按下播放。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-471">Press play in Unity.</span></span>
   * <span data-ttu-id="7f3e4-472">當移動觀景窗時，全像投影在 Unity 中的應該是他們在現實世界裡，相對於摘要您相機色彩。</span><span class="sxs-lookup"><span data-stu-id="7f3e4-472">When the camera is moved, holograms in Unity should be where they are in the real world relative to your camera color feed.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f3e4-473">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f3e4-473">See also</span></span>

* [<span data-ttu-id="7f3e4-474">混合的實境擷取</span><span class="sxs-lookup"><span data-stu-id="7f3e4-474">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="7f3e4-475">混合實境擷取適用於開發人員</span><span class="sxs-lookup"><span data-stu-id="7f3e4-475">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="7f3e4-476">在混合實境中共用體驗</span><span class="sxs-lookup"><span data-stu-id="7f3e4-476">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* [<span data-ttu-id="7f3e4-477">在 GitHub 上的 spectator 檢視 （預覽） 程式碼</span><span class="sxs-lookup"><span data-stu-id="7f3e4-477">Spectator View (Preview) code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [<span data-ttu-id="7f3e4-478">Spectator 檢視 （預覽） 原生程式碼在 GitHub 上</span><span class="sxs-lookup"><span data-stu-id="7f3e4-478">Spectator View (Preview) native code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [<span data-ttu-id="7f3e4-479">在 GitHub 上 spectator 檢視專業人員的程式碼</span><span class="sxs-lookup"><span data-stu-id="7f3e4-479">Spectator View Pro code on GitHub</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
