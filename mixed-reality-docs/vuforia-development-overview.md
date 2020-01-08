---
title: 搭配使用 Vuforia 與 Unity
description: 利用 Vuforia 在 Unity 中建立 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia、標記、座標、參考框架、追蹤
ms.openlocfilehash: 2d7cc27cd9a5fe9bb6502edaa6df0b7a80755049
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334473"
---
# <a name="using-vuforia-engine-with-unity"></a><span data-ttu-id="49130-104">搭配使用 Vuforia 引擎與 Unity</span><span class="sxs-lookup"><span data-stu-id="49130-104">Using Vuforia Engine with Unity</span></span>

<span data-ttu-id="49130-105">Vuforia Engine 為 HoloLens 提供了一項重要的功能–將 AR 體驗連線到環境中特定映射和物件的能力。</span><span class="sxs-lookup"><span data-stu-id="49130-105">Vuforia Engine brings an important capability to HoloLens – the power to connect AR experiences to specific images and objects in the environment.</span></span> <span data-ttu-id="49130-106">您可以使用這項功能，在產業企業的機械上重迭引導式逐步指示，或為實體產品或遊戲新增數位功能和體驗。</span><span class="sxs-lookup"><span data-stu-id="49130-106">You can use this capability to overlay guided step-by-step instructions on top of machinery for the industrial enterprise or add digital features and experiences to a physical product or game.</span></span>

<span data-ttu-id="49130-107">為了在開發 AR 體驗時擁有更大的彈性，Vuforia 引擎提供各種功能和目標。</span><span class="sxs-lookup"><span data-stu-id="49130-107">For greater flexibility when developing AR experiences, Vuforia Engine offers a broad range of features and targets.</span></span> <span data-ttu-id="49130-108">其中一個最新的功能是 Vuforia 模型目標，這是商業和產業用途的主要功能。</span><span class="sxs-lookup"><span data-stu-id="49130-108">One of our newest features, Vuforia Model Targets, is a key capability for both commercial and industrial uses.</span></span> <span data-ttu-id="49130-109">模型目標可讓應用程式辨識實體物件（例如機器、汽車或玩具），並根據 CAD 或數位3D 模型加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="49130-109">Model Targets allow applications to recognize physical objects like machines, automobiles or toys and track them based on a CAD or digital 3D model.</span></span> <span data-ttu-id="49130-110">對於產業用途，這項功能可以在工廠或在現場推出時，為元件工作者和服務技術人員提供 AR 工作指示和程式指引。</span><span class="sxs-lookup"><span data-stu-id="49130-110">For industrial uses, this feature can provide assembly workers and service technicians with AR work instructions and procedural guidance while in the factory or out in the field.</span></span>

<span data-ttu-id="49130-111">針對手機和平板電腦建立的現有 Vuforia 引擎應用程式，可以輕鬆地在 Unity 中設定以在 HoloLens 上執行。</span><span class="sxs-lookup"><span data-stu-id="49130-111">Existing Vuforia Engine apps that were built for phones and tablets can easily be configured in Unity to run on HoloLens.</span></span> <span data-ttu-id="49130-112">您甚至可以使用 Vuforia 引擎將新的 HoloLens 應用程式帶到 Windows 10 平板電腦上，例如 Surface Pro 和 Surface Book。</span><span class="sxs-lookup"><span data-stu-id="49130-112">You can even use Vuforia Engine to take your new HoloLens app to Windows 10 tablets such as the Surface Pro and Surface Book.</span></span>


## <a name="get-the-tools"></a><span data-ttu-id="49130-113">取得工具</span><span class="sxs-lookup"><span data-stu-id="49130-113">Get the tools</span></span>

<span data-ttu-id="49130-114">[安裝建議](install-the-tools.md)的 Visual Studio 和 unity 版本，然後將 unity 設定為使用 Visual Studio 和慣用的 IDE 和編譯器。</span><span class="sxs-lookup"><span data-stu-id="49130-114">[Install the recommended versions](install-the-tools.md) of Visual Studio and Unity and then configure Unity to use Visual Studio and the preferred IDE and compiler.</span></span> 

<span data-ttu-id="49130-115">安裝 Unity 時，請務必安裝「Windows Store IL2CPP 腳本後端」。</span><span class="sxs-lookup"><span data-stu-id="49130-115">When installing Unity, be sure to install the “Windows Store IL2CPP Scripting Backend”.</span></span>

<span data-ttu-id="49130-116">根據您的 Unity 版本而定，新增 Vuforia 引擎支援的運作方式會有所不同：</span><span class="sxs-lookup"><span data-stu-id="49130-116">Adding  Vuforia Engine Support works differently depending on your version of Unity:</span></span>
*   <span data-ttu-id="49130-117">Unity 2018.4：從 Vuforia 開發人員入口網站下載適用于 Unity 2018.4 的 Vuforia Engine 安裝程式</span><span class="sxs-lookup"><span data-stu-id="49130-117">Unity 2018.4: Download the Vuforia Engine installer for Unity 2018.4 from the Vuforia developer portal</span></span>
*   <span data-ttu-id="49130-118">Unity 2019.2：取得最新的[Vuforia 引擎封裝](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)</span><span class="sxs-lookup"><span data-stu-id="49130-118">Unity 2019.2: Get the latest [Vuforia Engine package](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)</span></span> 

## <a name="getting-started-with-vuforia-engine"></a><span data-ttu-id="49130-119">開始使用 Vuforia Engine</span><span class="sxs-lookup"><span data-stu-id="49130-119">Getting started with Vuforia Engine</span></span>

<span data-ttu-id="49130-120">學習使用 Vuforia Engine 搭配 HoloLens 的最佳起點是使用[Vuforia Engine HoloLens 範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)（可在 Unity 資產存放區中取得）。</span><span class="sxs-lookup"><span data-stu-id="49130-120">The best starting point for learning about using Vuforia Engine with HoloLens is with the [Vuforia Engine HoloLens sample](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (available in the Unity Asset Store).</span></span> <span data-ttu-id="49130-121">此範例會提供完整的 HoloLens 專案，包括可部署至 HoloLens 的預先設定場景。</span><span class="sxs-lookup"><span data-stu-id="49130-121">The sample provides a complete HoloLens project including pre-configured scenes that can be deployed to a HoloLens.</span></span>

<span data-ttu-id="49130-122">幕後會示範如何使用 Vuforia 的影像目標來辨識影像，並使用 HoloLens 體驗中的數位內容來增加它。</span><span class="sxs-lookup"><span data-stu-id="49130-122">The scenes show how to use Vuforia Image Targets to recognize an image and augment it with digital content in a HoloLens experience.</span></span> <span data-ttu-id="49130-123">Vuforia Engine Hololens 範例也包含一個場景，其中顯示在 HoloLens 上使用模型目標和 VuMarks 的情況。</span><span class="sxs-lookup"><span data-stu-id="49130-123">The Vuforia Engine Hololens Sample also includes a scene showing the usage of Model Targets and VuMarks on HoloLens.</span></span> <span data-ttu-id="49130-124">您可以輕鬆地在幕後替換自己的內容，以實驗如何建立使用 Vuforia 引擎的 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="49130-124">You can easily substitute your own content in the scenes to experiment with the creation of HoloLens apps that use Vuforia Engine.</span></span>



## <a name="configuring-a-vuforia-app-for-hololens"></a><span data-ttu-id="49130-125">設定適用于 HoloLens 的 Vuforia 應用程式</span><span class="sxs-lookup"><span data-stu-id="49130-125">Configuring a Vuforia App for HoloLens</span></span>

<span data-ttu-id="49130-126">開發適用于 HoloLens 的 Vuforia 引擎應用程式基本上與開發其他裝置的 Vuforia 引擎應用程式相同。</span><span class="sxs-lookup"><span data-stu-id="49130-126">Developing a Vuforia Engine app for HoloLens is fundamentally the same as developing Vuforia Engine apps for other devices.</span></span> <span data-ttu-id="49130-127">接著，您可以套用下列區段中所述的組建設定和設定。</span><span class="sxs-lookup"><span data-stu-id="49130-127">You can then apply the build settings and configurations described in the section below.</span></span> <span data-ttu-id="49130-128">這就是讓 Vuforia 引擎使用 HoloLens 空間對應和位置追蹤系統所需的一切。</span><span class="sxs-lookup"><span data-stu-id="49130-128">That’s all that’s needed to enable Vuforia Engine to work with the HoloLens spatial mapping and positional tracking systems.</span></span>

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a><span data-ttu-id="49130-129">建立並執行 HoloLens 的 Vuforia 引擎範例</span><span class="sxs-lookup"><span data-stu-id="49130-129">Build and Run the Vuforia Engine Sample for HoloLens</span></span>
1.  <span data-ttu-id="49130-130">從 Unity 資產存放區下載[適用于 HoloLens 的 Vuforia 引擎範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)</span><span class="sxs-lookup"><span data-stu-id="49130-130">Download the [Vuforia Engine Sample for HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) from the Unity Asset Store</span></span>
2.  <span data-ttu-id="49130-131">套用適用于[電源和效能的建議 Unity 引擎選項](performance-recommendations-for-unity.md)</span><span class="sxs-lookup"><span data-stu-id="49130-131">Apply the [recommended Unity engine options for power and performance](performance-recommendations-for-unity.md)</span></span>
3.  <span data-ttu-id="49130-132">將範例場景新增至組建中的場景。</span><span class="sxs-lookup"><span data-stu-id="49130-132">Add the sample scenes to Scenes in Build.</span></span>
4.  <span data-ttu-id="49130-133">在 [檔案 > 組建設定] 中，設定 "通用 Windows 平臺" 的平臺組建目標。</span><span class="sxs-lookup"><span data-stu-id="49130-133">Set your platform build target for “Universal Windows Platform” in File > Build Settings.</span></span>
5.  <span data-ttu-id="49130-134">選取下列平臺組建設定：</span><span class="sxs-lookup"><span data-stu-id="49130-134">Select the following platform build configuration settings:</span></span> 
   * <span data-ttu-id="49130-135">目標裝置 = HoloLens</span><span class="sxs-lookup"><span data-stu-id="49130-135">Target Device = HoloLens</span></span>
   * <span data-ttu-id="49130-136">組建類型 = D3D</span><span class="sxs-lookup"><span data-stu-id="49130-136">Build Type = D3D</span></span>
   * <span data-ttu-id="49130-137">SDK = 已安裝最新版本</span><span class="sxs-lookup"><span data-stu-id="49130-137">SDK = Latest Installed</span></span>
   * <span data-ttu-id="49130-138">Visual Studio 版本 = 最新安裝</span><span class="sxs-lookup"><span data-stu-id="49130-138">Visual Studio Version = Latest Installed</span></span>
   * <span data-ttu-id="49130-139">組建並在 = 本機電腦上執行</span><span class="sxs-lookup"><span data-stu-id="49130-139">Build and Run on = Local Machine</span></span>
6.  <span data-ttu-id="49130-140">在 [**播放程式設定**] 中定義唯一的**產品名稱**，以在安裝于 HoloLens 時做為應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="49130-140">Define a unique **Product Name**, in **Player Settings**, to serve as the name of the app when installed on the HoloLens.</span></span>
7.  <span data-ttu-id="49130-141">查看**Vuforia**增強的現實和**播放 > XR 設定**中**支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="49130-141">Check **Vuforia Augmented Reality** and **Virtual Reality Supported** in **Player Settings > XR Settings**</span></span>
8.  <span data-ttu-id="49130-142">此外，在 [ **XR 設定**] 下，確定 [Windows Mixed Reality] 已新增至**虛擬實境 sdk**清單</span><span class="sxs-lookup"><span data-stu-id="49130-142">Also under **XR Settings**, make sure that “Windows Mixed Reality” is added to the **Virtual Reality SDKs** List</span></span>
9.  <span data-ttu-id="49130-143">檢查播放 [設定] 中的下列功能 > 發佈設定</span><span class="sxs-lookup"><span data-stu-id="49130-143">Check the following Capabilities in Player Settings > Publish Settings</span></span> 
   * <span data-ttu-id="49130-144">InternetClient</span><span class="sxs-lookup"><span data-stu-id="49130-144">InternetClient</span></span>
   * <span data-ttu-id="49130-145">網路</span><span class="sxs-lookup"><span data-stu-id="49130-145">WebCam</span></span>
   * <span data-ttu-id="49130-146">SpatialPerception-如果您想要使用 Surface Observer API</span><span class="sxs-lookup"><span data-stu-id="49130-146">SpatialPerception - if you intend to use the Surface Observer API</span></span>
10. <span data-ttu-id="49130-147">選取 [組建] 以產生 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="49130-147">Select Build to generate a Visual Studio project</span></span>
11. <span data-ttu-id="49130-148">從 Visual Studio 建立可執行檔，並將它安裝在 HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="49130-148">Build the executable from Visual Studio and install it on your HoloLens</span></span>

<span data-ttu-id="49130-149">注意：從版本7.2 開始，HoloLens 的 Vuforia 引擎範例包含範例場景，包括模型目標的範例用法</span><span class="sxs-lookup"><span data-stu-id="49130-149">Note: Starting with version 7.2, the Vuforia Engine Sample for HoloLens includes a sample scene including example usage of Model Targets</span></span>

## <a name="the-vuforia-developer-portal"></a><span data-ttu-id="49130-150">Vuforia 開發人員入口網站</span><span class="sxs-lookup"><span data-stu-id="49130-150">The Vuforia Developer Portal</span></span>

<span data-ttu-id="49130-151">想要使用 Vuforia 引擎和 HoloLens 建立自己的 AR 經驗的開發人員，應該在 Vuforia 開發人員入口網站的[developer.vuforia.com](https://developer.vuforia.com/)註冊。</span><span class="sxs-lookup"><span data-stu-id="49130-151">Developers looking to create their own AR experiences with Vuforia Engine and HoloLens should sign up on our Vuforia Developer Portal at [developer.vuforia.com](https://developer.vuforia.com/).</span></span> <span data-ttu-id="49130-152">在入口網站中，開發人員可以存取[Vuforia Engine 論壇](https://developer.vuforia.com/forum)，他們可在其中加入社區討論、具有所有 Vuforia 引擎功能之深入檔的文檔[庫](https://library.vuforia.com/)，以及[Vuforia 目標管理員](https://developer.vuforia.com/target-manager)，讓使用者可以在其中建立自己的自訂目標。</span><span class="sxs-lookup"><span data-stu-id="49130-152">In the portal, developers have access to the [Vuforia Engine Forums](https://developer.vuforia.com/forum) where they can join community discussions, a [library](https://library.vuforia.com/) with in-depth documentation on all the Vuforia Engine Features, and the [Vuforia Target Manager](https://developer.vuforia.com/target-manager) where users can create their own custom Targets.</span></span> <span data-ttu-id="49130-153">開發人員也可以使用[Vuforia 授權管理員](https://developer.vuforia.com/license-manager)註冊免費的開發人員授權。</span><span class="sxs-lookup"><span data-stu-id="49130-153">Developers can also sign up for a free Developer License using the [Vuforia License Manager](https://developer.vuforia.com/license-manager).</span></span>

## <a name="extended-tracking-with-vuforia"></a><span data-ttu-id="49130-154">使用 Vuforia 擴充追蹤</span><span class="sxs-lookup"><span data-stu-id="49130-154">Extended tracking with Vuforia</span></span>

<span data-ttu-id="49130-155">即使目標已經不在查看中，[延伸追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)還是會維持追蹤。</span><span class="sxs-lookup"><span data-stu-id="49130-155">[Extended tracking](https://library.vuforia.com/articles/Training/Extended-Tracking) maintains tracking even when a target is no longer in view.</span></span> <span data-ttu-id="49130-156">當位置裝置追蹤器啟用時，會自動為所有目標啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="49130-156">It is automatically enabled for all targets when the Positional Device Tracker is enabled.</span></span> <span data-ttu-id="49130-157">若是 HoloLens 應用程式，位置裝置追蹤器會在 Unity 中自動啟動。</span><span class="sxs-lookup"><span data-stu-id="49130-157">For HoloLens applications, the Positional Device Tracker is started automatically in Unity.</span></span>

<span data-ttu-id="49130-158">Vuforia 引擎會自動 e-fuses 相機追蹤和 HoloLens 的空間追蹤的姿勢，以提供穩定的目標，而不受相機是否看過目標。</span><span class="sxs-lookup"><span data-stu-id="49130-158">Vuforia Engine automatically fuses the poses from camera tracking and HoloLens's spatial tracking to provide stable target poses independent of whether the target is seen by the camera or not.</span></span>

<span data-ttu-id="49130-159">因為程式會自動處理，所以開發人員不需要任何程式設計。</span><span class="sxs-lookup"><span data-stu-id="49130-159">Since the process is handled automatically, it does not require any programming by the developer.</span></span>


<span data-ttu-id="49130-160">**以下是此程式的高階描述：**</span><span class="sxs-lookup"><span data-stu-id="49130-160">**The following is a high-level description of the process:**</span></span>
1. <span data-ttu-id="49130-161">Vuforia 的目標追蹤器可識別目標</span><span class="sxs-lookup"><span data-stu-id="49130-161">Vuforia’s target Tracker recognizes the target</span></span>
2. <span data-ttu-id="49130-162">接著會初始化目標追蹤</span><span class="sxs-lookup"><span data-stu-id="49130-162">Target tracking is then initialized</span></span>
3. <span data-ttu-id="49130-163">系統會分析目標的位置和旋轉，為 HoloLens 提供健全的姿勢估計</span><span class="sxs-lookup"><span data-stu-id="49130-163">The position and rotation of the target are analyzed to provide a robust pose estimate for HoloLens</span></span>
4. <span data-ttu-id="49130-164">Vuforia 引擎會將目標的姿勢轉換成 HoloLens 空間對應座標空間</span><span class="sxs-lookup"><span data-stu-id="49130-164">Vuforia Engine transforms the target's pose into the HoloLens spatial mapping coordinate space</span></span>
5. <span data-ttu-id="49130-165">如果目標不再是 view，HoloLens 會接管追蹤。</span><span class="sxs-lookup"><span data-stu-id="49130-165">HoloLens takes over tracking if the target is no longer in view.</span></span> <span data-ttu-id="49130-166">當您再次查看目標時，Vuforia 將會繼續正確地追蹤影像和物件。</span><span class="sxs-lookup"><span data-stu-id="49130-166">Whenever you look again at the target, Vuforia will continue to track the images and objects accurately.</span></span>

<span data-ttu-id="49130-167">系統會將偵測到但不再處於 view 的目標，回報為 EXTENDED_TRACKED。</span><span class="sxs-lookup"><span data-stu-id="49130-167">Targets that are detected, but no longer in view, are reported as EXTENDED_TRACKED.</span></span> <span data-ttu-id="49130-168">在這些情況下，用於所有目標的 DefaultTrackableEventHandler 腳本會繼續轉譯擴充內容。</span><span class="sxs-lookup"><span data-stu-id="49130-168">In these cases, the DefaultTrackableEventHandler script that is used on all targets continues to render augmentation content.</span></span> <span data-ttu-id="49130-169">開發人員可以藉由執行自訂的可追蹤事件處理常式腳本來控制此行為。</span><span class="sxs-lookup"><span data-stu-id="49130-169">The developer can control this behavior by implementing a custom trackable event handler script.</span></span>


## <a name="performance-mode-with-vuforia-engine"></a><span data-ttu-id="49130-170">具有 Vuforia 引擎的效能模式</span><span class="sxs-lookup"><span data-stu-id="49130-170">Performance Mode with Vuforia Engine</span></span> 

<span data-ttu-id="49130-171">您可以透過 Vuforia 引擎來管理 HoloLens 的效能，以達到 AR 的範圍，並降低 CPU 上的工作負載。</span><span class="sxs-lookup"><span data-stu-id="49130-171">It is possible through the Vuforia Engine to manage the performance on the HoloLens to extent AR experiences and reduce the workload on the CPU.</span></span> <span data-ttu-id="49130-172">Vuforia 引擎提供三種可選取的模式：預設、用於優化速度，以及優化品質。</span><span class="sxs-lookup"><span data-stu-id="49130-172">The Vuforia Engine offers three modes that can be selected: default, for optimizing speed, and for optimizing quality.</span></span> 

*   <span data-ttu-id="49130-173">MODE_OPTIMIZE_SPEED 可讓您將 HoloLens 裝置上的工作負載最小化，而且很適合用來擴充 AR 的體驗。</span><span class="sxs-lookup"><span data-stu-id="49130-173">MODE_OPTIMIZE_SPEED lets you minimize the workload on the HoloLens device and is great for extending AR experiences.</span></span> <span data-ttu-id="49130-174">在應用程式正在追蹤靜態物件/目標的情況下，建議使用此選項。</span><span class="sxs-lookup"><span data-stu-id="49130-174">It is recommended for situations where the app is tracking static objects/targets.</span></span>
*   <span data-ttu-id="49130-175">MODE_DEFAULT 是正常模式，可用於大部分的案例中。</span><span class="sxs-lookup"><span data-stu-id="49130-175">MODE_DEFAULT is the normal mode which can be used in most scenarios.</span></span>
*   <span data-ttu-id="49130-176">MODE_OPTIMIZE_QUALITY 更適合用來追蹤您預期會挑選的可移動目標或模型目標。</span><span class="sxs-lookup"><span data-stu-id="49130-176">MODE_OPTIMIZE_QUALITY is better for tracking movable targets or model targets you expect to be picked up.</span></span>

<span data-ttu-id="49130-177">**設定模式**</span><span class="sxs-lookup"><span data-stu-id="49130-177">**Setting the mode**</span></span>

<span data-ttu-id="49130-178">若要變更 Unity 中的效能模式，請流覽至 [Vuforia 設定] （Ctrl + Shift + V/Cmd + Shift + V），其位於 ARCamera GameObject 中的元件。</span><span class="sxs-lookup"><span data-stu-id="49130-178">To change the performance mode in Unity, navigate to Vuforia Configuration (Ctrl+Shift+V / Cmd+Shift+V) that is located as a component in the ARCamera GameObject.</span></span> 
*   <span data-ttu-id="49130-179">選取 [相機裝置模式] 的下拉式功能表，然後選取三個選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="49130-179">Select the dropdown menu for Camera Device Mode and select one of the three options.</span></span>


## <a name="see-also"></a><span data-ttu-id="49130-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="49130-180">See also</span></span>
* [<span data-ttu-id="49130-181">安裝工具</span><span class="sxs-lookup"><span data-stu-id="49130-181">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="49130-182">座標系統</span><span class="sxs-lookup"><span data-stu-id="49130-182">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="49130-183">空間對應</span><span class="sxs-lookup"><span data-stu-id="49130-183">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="49130-184">Unity 中的相機</span><span class="sxs-lookup"><span data-stu-id="49130-184">Camera in Unity</span></span>](camera-in-unity.md)
* [<span data-ttu-id="49130-185">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="49130-185">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="49130-186">Vuforia 檔：在 Unity 中針對 Windows 10 進行開發</span><span class="sxs-lookup"><span data-stu-id="49130-186">Vuforia documentation: Developing for Windows 10 in Unity</span></span>](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [<span data-ttu-id="49130-187">Vuforia 檔：如何安裝 Vuforia Unity 延伸模組</span><span class="sxs-lookup"><span data-stu-id="49130-187">Vuforia documentation: How to install the Vuforia Unity extension</span></span>](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [<span data-ttu-id="49130-188">Vuforia 檔：使用 Unity 中的 HoloLens 範例</span><span class="sxs-lookup"><span data-stu-id="49130-188">Vuforia documentation: Working with the HoloLens sample in Unity</span></span>](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [<span data-ttu-id="49130-189">Vuforia 檔： Vuforia 中的延伸追蹤</span><span class="sxs-lookup"><span data-stu-id="49130-189">Vuforia documentation: Extended tracking in Vuforia</span></span>](https://library.vuforia.com/articles/Training/Extended-Tracking)
