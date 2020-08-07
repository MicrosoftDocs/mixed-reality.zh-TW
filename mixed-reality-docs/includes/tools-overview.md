# <a name="unity"></a>[<span data-ttu-id="bd462-101">Unity</span><span class="sxs-lookup"><span data-stu-id="bd462-101">Unity</span></span>](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="bd462-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="bd462-103">1. Download the latest version</span></span>

<span data-ttu-id="bd462-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span> 
* <span data-ttu-id="bd462-105">目前建議使用 **Unity 2019**，這是以下 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="bd462-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="bd462-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="bd462-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="bd462-107">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="bd462-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="bd462-109">[混合實境工具組](../mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="bd462-109">[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="bd462-110">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="bd462-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="bd462-111">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bd462-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="bd462-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="bd462-113">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="bd462-113">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="bd462-114">如果您不想使用適用於 Unity 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="bd462-114">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="bd462-115">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="bd462-115">Other tools [optional]</span></span>
* <span data-ttu-id="bd462-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="bd462-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="bd462-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="bd462-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bd462-118">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bd462-118">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="bd462-119">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bd462-119">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bd462-120">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bd462-120">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bd462-121">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bd462-121">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="bd462-122">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-122">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bd462-123">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-123">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bd462-124">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bd462-124">For HoloLens development</span></span>

<span data-ttu-id="bd462-125">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-125">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bd462-126">如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bd462-126">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bd462-127">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="bd462-127">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="bd462-128">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-128">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bd462-129">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bd462-129">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bd462-130">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bd462-130">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bd462-131">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bd462-131">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bd462-132">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bd462-132">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bd462-133">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bd462-133">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bd462-134">最低需求</span><span class="sxs-lookup"><span data-stu-id="bd462-134">Minimum</span></span></th><th> <span data-ttu-id="bd462-135">建議</span><span class="sxs-lookup"><span data-stu-id="bd462-135">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bd462-136">處理器</span><span class="sxs-lookup"><span data-stu-id="bd462-136">Processor</span></span></td><td> <span data-ttu-id="bd462-137"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bd462-137"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bd462-138"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bd462-138"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-139">GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-139">GPU</span></span></td><td> <span data-ttu-id="bd462-140"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-140"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bd462-141"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-141"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-142">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bd462-142">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bd462-143">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bd462-143">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-144">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bd462-144">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bd462-145">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-145">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-146">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-146">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-147">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bd462-147">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-148">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bd462-148">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bd462-149">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bd462-149">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-150">Memory</span><span class="sxs-lookup"><span data-stu-id="bd462-150">Memory</span></span></td><td> <span data-ttu-id="bd462-151">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-151">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bd462-152">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-152">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-153">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bd462-153">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bd462-154">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bd462-154">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-155">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-155">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-156">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bd462-156">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-157">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bd462-157">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bd462-158">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bd462-158">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="bd462-159">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="bd462-159">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd462-160">開始您的 Unity 旅程</span><span class="sxs-lookup"><span data-stu-id="bd462-160">Start your Unity journey</span></span>](../unity-development-overview.md)

# <a name="unreal"></a>[<span data-ttu-id="bd462-161">Unreal</span><span class="sxs-lookup"><span data-stu-id="bd462-161">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="bd462-163">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="bd462-163">1. Download the latest version</span></span>

<span data-ttu-id="bd462-164">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="bd462-164">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="bd462-165">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="bd462-165">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="bd462-167">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="bd462-167">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="bd462-168">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="bd462-168">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="bd462-169">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-169">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bd462-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="bd462-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="bd462-171">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="bd462-171">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="bd462-172">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="bd462-172">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="bd462-173">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="bd462-173">Other tools [optional]</span></span>
* <span data-ttu-id="bd462-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="bd462-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="bd462-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="bd462-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bd462-176">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bd462-176">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="bd462-177">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bd462-177">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bd462-178">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bd462-178">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bd462-179">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bd462-179">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="bd462-180">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-180">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bd462-181">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-181">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bd462-182">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bd462-182">For HoloLens development</span></span>

<span data-ttu-id="bd462-183">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-183">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bd462-184">如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bd462-184">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bd462-185">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-185">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bd462-186">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bd462-186">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bd462-187">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bd462-187">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bd462-188">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bd462-188">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bd462-189">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bd462-189">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bd462-190">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bd462-190">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bd462-191">最低需求</span><span class="sxs-lookup"><span data-stu-id="bd462-191">Minimum</span></span></th><th> <span data-ttu-id="bd462-192">建議</span><span class="sxs-lookup"><span data-stu-id="bd462-192">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bd462-193">處理器</span><span class="sxs-lookup"><span data-stu-id="bd462-193">Processor</span></span></td><td> <span data-ttu-id="bd462-194"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bd462-194"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bd462-195"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bd462-195"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-196">GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-196">GPU</span></span></td><td> <span data-ttu-id="bd462-197"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-197"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bd462-198"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-198"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-199">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bd462-199">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bd462-200">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bd462-200">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-201">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bd462-201">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bd462-202">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-202">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-203">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-203">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-204">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bd462-204">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-205">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bd462-205">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bd462-206">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bd462-206">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-207">Memory</span><span class="sxs-lookup"><span data-stu-id="bd462-207">Memory</span></span></td><td> <span data-ttu-id="bd462-208">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-208">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bd462-209">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-209">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-210">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bd462-210">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bd462-211">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bd462-211">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-212">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-212">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-213">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bd462-213">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-214">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bd462-214">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bd462-215">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bd462-215">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="bd462-216">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="bd462-216">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd462-217">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="bd462-217">Start your Unreal journey</span></span>](../unreal-development-overview.md)

# <a name="native-openxr"></a>[<span data-ttu-id="bd462-218">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="bd462-218">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="bd462-220">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="bd462-220">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="bd462-221">您可以在[開始使用 OpenXR](../openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="bd462-221">You can find everything you need to begin development in the [Getting started with OpenXR](../openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bd462-222">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bd462-222">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="bd462-223">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bd462-223">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bd462-224">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bd462-224">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bd462-225">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bd462-225">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bd462-226">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bd462-226">For HoloLens development</span></span>

<span data-ttu-id="bd462-227">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-227">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bd462-228">如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bd462-228">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bd462-229">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-229">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="bd462-230">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd462-230">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bd462-231">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bd462-231">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bd462-232">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bd462-232">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bd462-233">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bd462-233">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bd462-234">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bd462-234">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bd462-235">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bd462-235">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bd462-236">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bd462-236">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bd462-237">最低需求</span><span class="sxs-lookup"><span data-stu-id="bd462-237">Minimum</span></span></th><th> <span data-ttu-id="bd462-238">建議</span><span class="sxs-lookup"><span data-stu-id="bd462-238">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bd462-239">處理器</span><span class="sxs-lookup"><span data-stu-id="bd462-239">Processor</span></span></td><td> <span data-ttu-id="bd462-240"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bd462-240"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bd462-241"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bd462-241"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-242">GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-242">GPU</span></span></td><td> <span data-ttu-id="bd462-243"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-243"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bd462-244"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bd462-244"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-245">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bd462-245">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bd462-246">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bd462-246">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-247">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bd462-247">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bd462-248">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-248">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-249">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-249">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-250">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bd462-250">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-251">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bd462-251">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bd462-252">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bd462-252">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-253">Memory</span><span class="sxs-lookup"><span data-stu-id="bd462-253">Memory</span></span></td><td> <span data-ttu-id="bd462-254">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-254">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bd462-255">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bd462-255">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-256">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bd462-256">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bd462-257">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bd462-257">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-258">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bd462-258">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bd462-259">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bd462-259">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd462-260">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bd462-260">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bd462-261">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bd462-261">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="bd462-262">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="bd462-262">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd462-263">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="bd462-263">Start your Native journey</span></span>](../directx-development-overview.md)


