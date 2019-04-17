---
title: 使用 HoloLens 模擬器
description: HoloLens 模擬器可讓您測試您的電腦，而不需要實體 HoloLens 上的混合的實境應用程式。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、 模擬器
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596685"
---
# <a name="using-the-hololens-emulator"></a><span data-ttu-id="f5b61-104">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="f5b61-104">Using the HoloLens emulator</span></span>

<span data-ttu-id="f5b61-105">HoloLens 模擬器可讓您測試您的電腦，而不需要實體 HoloLens 上全像攝影版的應用程式，並隨附 HoloLens 的開發工具組。</span><span class="sxs-lookup"><span data-stu-id="f5b61-105">The HoloLens emulator allows you to test holographic apps on your PC without a physical HoloLens and comes with the HoloLens development toolset.</span></span> <span data-ttu-id="f5b61-106">模擬器會使用 HYPER-V 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-106">The emulator uses a Hyper-V virtual machine.</span></span> <span data-ttu-id="f5b61-107">通常會由 HoloLens 上感應器的人力和環境輸入是改為模擬使用您的鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-107">The human and environmental inputs that would usually be read by the sensors on the HoloLens are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="f5b61-108">應用程式不需要修改，才能在模擬器上執行，而且不知道它們不真正的 HoloLens 上執行。</span><span class="sxs-lookup"><span data-stu-id="f5b61-108">Apps don't need to be modified to run on the emulator and don't know that they aren't running on a real HoloLens.</span></span>

<span data-ttu-id="f5b61-109">如果您想要開發適用於桌面的電腦的 Windows Mixed Reality 沈浸式 (VR) 耳機應用程式或遊戲，請參閱[Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)，這可讓您改為模擬桌面耳機。</span><span class="sxs-lookup"><span data-stu-id="f5b61-109">If you're looking to develop Windows Mixed Reality immersive (VR) headset apps or games for desktop PCs, check out the [Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md), which lets you simulate desktop headsets instead.</span></span>

> [!NOTE]
> <span data-ttu-id="f5b61-110">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="f5b61-110">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="installing-the-hololens-emulator"></a><span data-ttu-id="f5b61-111">安裝 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="f5b61-111">Installing the HoloLens emulator</span></span>

<span data-ttu-id="f5b61-112">下載[HoloLens （第 1 代） 模擬器] 和 [全像攝影版的專案範本](https://go.microsoft.com/fwlink/?linkid=2065980)。</span><span class="sxs-lookup"><span data-stu-id="f5b61-112">Download the [HoloLens (1st gen) emulator and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2065980).</span></span>

<span data-ttu-id="f5b61-113">您可以找到舊版組建的 HoloLens 模擬器[HoloLens 模擬器封存](hololens-emulator-archive.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="f5b61-113">You can find older builds of the HoloLens emulator on the [HoloLens emulator archive](hololens-emulator-archive.md) page.</span></span>

### <a name="hololens-emulator-system-requirements"></a><span data-ttu-id="f5b61-114">HoloLens 模擬器系統需求</span><span class="sxs-lookup"><span data-stu-id="f5b61-114">HoloLens emulator system requirements</span></span>

<span data-ttu-id="f5b61-115">HoloLens 模擬器以 HYPER-V 為基礎，並使用 RemoteFx 的硬體加速的圖形。</span><span class="sxs-lookup"><span data-stu-id="f5b61-115">The HoloLens emulator is based on Hyper-V and uses RemoteFx for hardware accelerated graphics.</span></span> <span data-ttu-id="f5b61-116">若要使用模擬器，請確定您的電腦符合下列硬體需求：</span><span class="sxs-lookup"><span data-stu-id="f5b61-116">To use the emulator, make sure your PC meets these hardware requirements:</span></span>
* <span data-ttu-id="f5b61-117">64 位元 Windows 10 Pro、 Enterprise 或教育版</span><span class="sxs-lookup"><span data-stu-id="f5b61-117">64-bit Windows 10 Pro, Enterprise, or Education</span></span> 
    >[!NOTE]
    ><span data-ttu-id="f5b61-118">Windows 10 家用版不支援 HYPER-V 或 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="f5b61-118">Windows 10 Home edition does not support Hyper-V or the HoloLens emulator</span></span>
* <span data-ttu-id="f5b61-119">64 位元 CPU</span><span class="sxs-lookup"><span data-stu-id="f5b61-119">64-bit CPU</span></span>
* <span data-ttu-id="f5b61-120">CPU 4 個核心 （或多個 Cpu，總共有 4 個核心）</span><span class="sxs-lookup"><span data-stu-id="f5b61-120">CPU with 4 cores (or multiple CPUs with a total of 4 cores)</span></span>
* <span data-ttu-id="f5b61-121">8 GB 的 RAM 或以上</span><span class="sxs-lookup"><span data-stu-id="f5b61-121">8 GB of RAM or more</span></span>
* <span data-ttu-id="f5b61-122">在 BIOS 中必須是下列功能[支援，並啟用](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span><span class="sxs-lookup"><span data-stu-id="f5b61-122">In the BIOS, the following features must be [supported and enabled](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span></span>
   * <span data-ttu-id="f5b61-123">硬體協助虛擬化</span><span class="sxs-lookup"><span data-stu-id="f5b61-123">Hardware-assisted virtualization</span></span>
   * <span data-ttu-id="f5b61-124">第二層位址轉譯 (SLAT)</span><span class="sxs-lookup"><span data-stu-id="f5b61-124">Second Level Address Translation (SLAT)</span></span>
   * <span data-ttu-id="f5b61-125">硬體型資料執行防止 (DEP)。</span><span class="sxs-lookup"><span data-stu-id="f5b61-125">Hardware-based Data Execution Prevention (DEP)</span></span>
* <span data-ttu-id="f5b61-126">GPU 需求 （模擬器可能會使用不支援的 GPU，但將會明顯變慢）</span><span class="sxs-lookup"><span data-stu-id="f5b61-126">GPU requirements (the emulator might work with an unsupported GPU, but will be significantly slower)</span></span>
   * <span data-ttu-id="f5b61-127">DirectX 11.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="f5b61-127">DirectX 11.0 or later</span></span>
   * <span data-ttu-id="f5b61-128">WDDM 1.2 驅動程式或更新版本</span><span class="sxs-lookup"><span data-stu-id="f5b61-128">WDDM 1.2 driver or later</span></span>

<span data-ttu-id="f5b61-129">如果您的系統符合上述需求，**請確定您的系統上，已啟用 「 HYPER-V 」 功能**透過 控制台-> 程式-> 程式和功能-> 上的 開啟 Windows 功能，或關閉-> 確認「 HYPER-V 」 已選取的模擬器安裝才能成功。</span><span class="sxs-lookup"><span data-stu-id="f5b61-129">If your system meets the above requirements, **please ensure that the "Hyper-V" feature has been enabled on your system** through Control Panel -> Programs -> Programs and Features -> Turn Windows Features on or off -> ensure that "Hyper-V" is selected for the Emulator installation to be successful.</span></span>

### <a name="installation-troubleshooting"></a><span data-ttu-id="f5b61-130">安裝疑難排解</span><span class="sxs-lookup"><span data-stu-id="f5b61-130">Installation troubleshooting</span></span>

<span data-ttu-id="f5b61-131">安裝模擬器，您需要時，您可能會看到錯誤 *「 Visual Studio 2015 Update 1 及 UWP 工具 1.2 版 「*。</span><span class="sxs-lookup"><span data-stu-id="f5b61-131">You may see an error while installing the emulator that you need *"Visual Studio 2015 Update 1 and UWP tools version 1.2"*.</span></span> <span data-ttu-id="f5b61-132">有三個可能的原因，此錯誤：</span><span class="sxs-lookup"><span data-stu-id="f5b61-132">There are three possible causes of this error:</span></span>
* <span data-ttu-id="f5b61-133">您沒有 Visual Studio （Visual Studio 2017 或 Visual Studio 2015 Update 1 或更新版本） 不夠新版本。</span><span class="sxs-lookup"><span data-stu-id="f5b61-133">You do not have a recent enough version of Visual Studio (Visual Studio 2017 or Visual Studio 2015 Update 1 or later).</span></span> <span data-ttu-id="f5b61-134">若要修正此問題，安裝最新版的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f5b61-134">To correct this, install the latest release of Visual Studio.</span></span>
* <span data-ttu-id="f5b61-135">您擁有的版本不夠新，Visual Studio 中，但您不需要安裝的通用 Windows 平台 (UWP) 工具。</span><span class="sxs-lookup"><span data-stu-id="f5b61-135">You have a recent enough version of Visual Studio, but you do not have the Universal Windows Platform (UWP) tools installed.</span></span> <span data-ttu-id="f5b61-136">這是適用於 Visual Studio 的選用功能。</span><span class="sxs-lookup"><span data-stu-id="f5b61-136">This is an optional feature for Visual Studio.</span></span>

<span data-ttu-id="f5b61-137">您可能也會看到安裝模擬器上非-PRO/Enterprise/教育 SKU 的 Windows 錯誤，或如果您沒有 HYPER-V 功能啟用。</span><span class="sxs-lookup"><span data-stu-id="f5b61-137">You may also see an error installing the emulator on a non-PRO/Enterprise/Education SKU of Windows or if you do not have Hyper-V feature enabled.</span></span>
* <span data-ttu-id="f5b61-138">請閱讀[系統需求](#hololens-emulator-system-requirements)的一組完整的需求一節。</span><span class="sxs-lookup"><span data-stu-id="f5b61-138">Please read the [system requirements](#hololens-emulator-system-requirements) section above for a complete set of requirements.</span></span>
* <span data-ttu-id="f5b61-139">請也確保您的系統上，已啟用 HYPER-V 功能。</span><span class="sxs-lookup"><span data-stu-id="f5b61-139">Please also ensure that Hyper-V feature has been enabled on your system.</span></span>

## <a name="deploying-apps-to-the-hololens-emulator"></a><span data-ttu-id="f5b61-140">應用程式部署到 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="f5b61-140">Deploying apps to the HoloLens emulator</span></span>

1. <span data-ttu-id="f5b61-141">載入您的應用程式解決方案，在 Visual Studio 2015。</span><span class="sxs-lookup"><span data-stu-id="f5b61-141">Load your app solution in Visual Studio 2015.</span></span>
    >[!NOTE]
    ><span data-ttu-id="f5b61-142">當使用 Unity 時，從 Unity 建置您的專案，然後如往常般將建置的方案載入至 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f5b61-142">When using Unity, build your project from Unity and then load the built solution into Visual Studio as usual.</span></span>
2. <span data-ttu-id="f5b61-143">請確定在平台設定為**x86**。</span><span class="sxs-lookup"><span data-stu-id="f5b61-143">Ensure the Platform is set to **x86**.</span></span>
3. <span data-ttu-id="f5b61-144">選取  **HoloLens 模擬器**作為偵錯的目標裝置。</span><span class="sxs-lookup"><span data-stu-id="f5b61-144">Select the **HoloLens Emulator** as the target device for debugging.</span></span>
4. <span data-ttu-id="f5b61-145">移至**偵錯 > 啟動偵錯**或按**F5**啟動模擬器和部署您的應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f5b61-145">Go to **Debug > Start Debugging** or press **F5** to launch the emulator and deploy your app for debugging.</span></span>

<span data-ttu-id="f5b61-146">模擬器可能需要一分鐘或更多以第一次啟動時開機。</span><span class="sxs-lookup"><span data-stu-id="f5b61-146">The emulator may take a minute or more to boot when you first start it.</span></span> <span data-ttu-id="f5b61-147">我們建議您保持模擬器開啟偵錯工作階段期間讓您可以快速地將應用程式部署到執行中的模擬器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-147">We recommend that you keep the emulator open during your debugging session so you can quickly deploy apps to the running emulator.</span></span>

## <a name="basic-emulator-input"></a><span data-ttu-id="f5b61-148">基本的模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="f5b61-148">Basic emulator input</span></span>

<span data-ttu-id="f5b61-149">控制模擬器是非常類似於許多常見的 3D 視訊遊戲。</span><span class="sxs-lookup"><span data-stu-id="f5b61-149">Controlling the emulator is very similar to many common 3D video games.</span></span> <span data-ttu-id="f5b61-150">有可用的輸入的選項使用鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-150">There are input options available using the keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="f5b61-151">您可以將導向穿著 HoloLens 的模擬使用者動作控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-151">You control the emulator by directing the actions of a simulated user wearing a HoloLens.</span></span> <span data-ttu-id="f5b61-152">您的動作移動周圍的模擬的使用者並在模擬器中執行的應用程式回應在實際裝置上所顯示的一樣。</span><span class="sxs-lookup"><span data-stu-id="f5b61-152">Your actions move that simulated user around and apps running in the emulator respond like they would on a real device.</span></span>
* <span data-ttu-id="f5b61-153">**上一步，向前保留，並以滑鼠右鍵**-使用 W、 A、 S 和 D 鍵盤或 Xbox 控制器上的左搖桿上的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f5b61-153">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="f5b61-154">**查閱，向下、 左、 並以滑鼠右鍵**-按一下並拖曳滑鼠，使用方向鍵在鍵盤或 Xbox 控制器上正確的隨身碟上。</span><span class="sxs-lookup"><span data-stu-id="f5b61-154">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="f5b61-155">**空中點選手勢**-按一下滑鼠右鍵，在鍵盤上按 Enter 鍵或使用 Xbox 控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f5b61-155">**Air tap gesture** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="f5b61-156">**百花齊放筆勢**-在鍵盤上按 Windows 鍵或 F2 鍵或按下 B 上的 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-156">**Bloom gesture** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="f5b61-157">**另一方面移動捲動**-按住 Alt 鍵，請按住滑鼠按鈕，並拖曳滑鼠，增加 / 減少，或 Xbox 控制器中按住正確的觸發程序和一個按鈕並向上和向下移動右隨身碟。</span><span class="sxs-lookup"><span data-stu-id="f5b61-157">**Hand movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="anatomy-of-the-hololens-emulator"></a><span data-ttu-id="f5b61-158">HoloLens 模擬器的結構</span><span class="sxs-lookup"><span data-stu-id="f5b61-158">Anatomy of the HoloLens emulator</span></span>

### <a name="main-window"></a><span data-ttu-id="f5b61-159">主視窗</span><span class="sxs-lookup"><span data-stu-id="f5b61-159">Main window</span></span>

<span data-ttu-id="f5b61-160">當模擬器啟動時，您會看到一個可顯示 HoloLens OS 視窗。</span><span class="sxs-lookup"><span data-stu-id="f5b61-160">When the emulator launches, you will see a window which displays the HoloLens OS.</span></span>

![HoloLens 模擬器主視窗](images/emulator-890px.png)

### <a name="toolbar"></a><span data-ttu-id="f5b61-162">工具列</span><span class="sxs-lookup"><span data-stu-id="f5b61-162">Toolbar</span></span>

<span data-ttu-id="f5b61-163">在主視窗的右邊，您會發現模擬器工具列。</span><span class="sxs-lookup"><span data-stu-id="f5b61-163">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="f5b61-164">工具列包含下列按鈕：</span><span class="sxs-lookup"><span data-stu-id="f5b61-164">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="f5b61-165">![關閉圖示](images/emulator-close.png)**關閉**:關閉模擬器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-165">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="f5b61-166">![最小化 圖示](images/emulator-minimize.png)**最小化**:最小化 [模擬器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f5b61-166">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="f5b61-167">![人性化的輸入的圖示](images/emulator-control.png)**人力輸入**:滑鼠和鍵盤用來模擬人類[輸入至模擬器](#basic-emulator-input)。</span><span class="sxs-lookup"><span data-stu-id="f5b61-167">![Human input icon](images/emulator-control.png) **Human Input**: Mouse and Keyboard are used to simulate human [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="f5b61-168">![鍵盤和滑鼠輸入的圖示](images/emulator-input.png)**鍵盤和滑鼠輸入**:鍵盤和滑鼠輸入會直接傳遞到 HoloLens 作業系統做為鍵盤和滑鼠事件連線藍芽鍵盤和滑鼠。</span><span class="sxs-lookup"><span data-stu-id="f5b61-168">![Keyboard and mouse input icon](images/emulator-input.png) **Keyboard and Mouse Input**: Keyboard and mouse input are passed directly to the HoloLens OS as keyboard and mouse events as if you connected a Bluetooth keyboard and mouse.</span></span>
* <span data-ttu-id="f5b61-169">![全螢幕圖示](images/emulator-fit.png)**全螢幕**:符合的模擬器畫面。</span><span class="sxs-lookup"><span data-stu-id="f5b61-169">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="f5b61-170">![顯示比例 圖示](images/emulator-zoom.png)**縮放**:放大及縮小，請讓模擬器。</span><span class="sxs-lookup"><span data-stu-id="f5b61-170">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="f5b61-171">![説明圖示](images/emulator-help.png)**協助**:開啟模擬器的說明。</span><span class="sxs-lookup"><span data-stu-id="f5b61-171">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="f5b61-172">![開啟裝置入口網站 圖示](images/emulator-deviceportal.png)**開啟裝置入口網站**:開啟 Windows Device Portal HoloLens os 在模擬器中。</span><span class="sxs-lookup"><span data-stu-id="f5b61-172">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="f5b61-173">![工具圖示](images/emulator-tools.png)**工具**:開啟**其他工具**窗格。</span><span class="sxs-lookup"><span data-stu-id="f5b61-173">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-tab"></a><span data-ttu-id="f5b61-174">模擬 索引標籤</span><span class="sxs-lookup"><span data-stu-id="f5b61-174">Simulation tab</span></span>

<span data-ttu-id="f5b61-175">中的 預設 索引標籤**額外的工具** 窗格是**模擬** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5b61-175">The default tab within the **Additional Tools** pane is the **Simulation** tab.</span></span>

![HoloLens 模擬器 [其他工具] 窗格](images/emulator-simulation-500px.png)

<span data-ttu-id="f5b61-177">[模擬] 索引標籤會顯示模擬的感應器用來驅動 HoloLens OS 在模擬器中的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="f5b61-177">The Simulation tab shows the current state of the simulated sensors used to drive the HoloLens OS within the emulator.</span></span> <span data-ttu-id="f5b61-178">將滑鼠停留在 [模擬] 索引標籤中的任何值，將會提供工具提示描述如何控制該值。</span><span class="sxs-lookup"><span data-stu-id="f5b61-178">Hovering over any value in the Simulation tab will provide a tooltip describing how to control that value.</span></span>

### <a name="room-tab"></a><span data-ttu-id="f5b61-179">空間索引標籤</span><span class="sxs-lookup"><span data-stu-id="f5b61-179">Room tab</span></span>

<span data-ttu-id="f5b61-180">模擬器會模擬世界空間對應網狀結構與模擬"聊天室"形式的輸入。</span><span class="sxs-lookup"><span data-stu-id="f5b61-180">The emulator simulates world input in the form of the spatial mapping mesh from simulated "rooms".</span></span> <span data-ttu-id="f5b61-181">此索引標籤可讓您挑選的空間可載入而不是預設的空間。</span><span class="sxs-lookup"><span data-stu-id="f5b61-181">This tab lets you pick which room to load instead of the default room.</span></span>

![HoloLens 模擬器 '聊天室' 索引標籤](images/emulator-room-500px.png)

<span data-ttu-id="f5b61-183">模擬的聊天室可用於在多個環境中測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5b61-183">Simulated rooms are useful for testing your app in multiple environments.</span></span> <span data-ttu-id="f5b61-184">數個房間隨附於模擬器，一旦您安裝模擬時，您會發現這些 %programfiles(x86) %\Program 檔案 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 中。</span><span class="sxs-lookup"><span data-stu-id="f5b61-184">Several rooms are shipped with the emulator and once you install the emulation, you will find them in %ProgramFiles(x86)%\Program Files (x86)\Microsoft XDE\10.0.11082.0\Plugins\Rooms.</span></span> <span data-ttu-id="f5b61-185">所有這些聊天室使用 HoloLens 的實際環境中所擷取的：</span><span class="sxs-lookup"><span data-stu-id="f5b61-185">All of these rooms were captured in real environments using a HoloLens:</span></span>
* <span data-ttu-id="f5b61-186">**DefaultRoom.xef** -電視、 咖啡桌，與兩個 sofas 小型起居室的絨布。</span><span class="sxs-lookup"><span data-stu-id="f5b61-186">**DefaultRoom.xef** - A small living room with a TV, coffee table, and two sofas.</span></span> <span data-ttu-id="f5b61-187">當您啟動模擬器時，請載入預設。</span><span class="sxs-lookup"><span data-stu-id="f5b61-187">Loaded by default when you start the emulator.</span></span>
* <span data-ttu-id="f5b61-188">**Bedroom1.xef** -小型臥室與支援人員。</span><span class="sxs-lookup"><span data-stu-id="f5b61-188">**Bedroom1.xef** - A small bedroom with a desk.</span></span>
* <span data-ttu-id="f5b61-189">**Bedroom2.xef** -臥室皇后大小平台、 與衣櫃、 nightstands，walk-in 衣櫥。</span><span class="sxs-lookup"><span data-stu-id="f5b61-189">**Bedroom2.xef** - A bedroom with a queen size bed, dresser, nightstands, and walk-in closet.</span></span>
* <span data-ttu-id="f5b61-190">**GreatRoom.xef** -客廳、 餐桌，與廚房的大型的開放空間絕佳空間。</span><span class="sxs-lookup"><span data-stu-id="f5b61-190">**GreatRoom.xef** - A large open space great room with living room, dining table, and kitchen.</span></span>
* <span data-ttu-id="f5b61-191">**LivingRoom.xef** -起居室的絨布壁爐、 沙發、 armchairs，以及具有花瓶的咖啡資料表。</span><span class="sxs-lookup"><span data-stu-id="f5b61-191">**LivingRoom.xef** - A living room with a fireplace, sofa, armchairs, and a coffee table with a vase.</span></span>

<span data-ttu-id="f5b61-192">您也可以記錄使用的模擬頁面在模擬器中使用您自己聊天室[Windows Device Portal](using-the-windows-device-portal.md)您 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="f5b61-192">You can also record your own rooms to use in the emulator using the Simulation page of the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens.</span></span>

<span data-ttu-id="f5b61-193">在模擬器中，您只會看到全像投影您轉譯，並將不會看到全像投影背後模擬的空間。</span><span class="sxs-lookup"><span data-stu-id="f5b61-193">On the emulator, you will only see holograms that you render and you will not see the simulated room behind the holograms.</span></span> <span data-ttu-id="f5b61-194">這是相較於真正的 HoloLens，您看到兩者混合在一起。</span><span class="sxs-lookup"><span data-stu-id="f5b61-194">This is in contrast to the real HoloLens where you see both blended together.</span></span> <span data-ttu-id="f5b61-195">如果您想要看到模擬的聊天室 HoloLens 模擬器中，您必須更新您的應用程式，以轉譯場景中的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="f5b61-195">If you want to see the simulated room in the HoloLens emulator, you will need to update your app to render the spatial mapping mesh in the scene.</span></span>

### <a name="account-tab"></a><span data-ttu-id="f5b61-196">[帳戶] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="f5b61-196">Account Tab</span></span>

<span data-ttu-id="f5b61-197">[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f5b61-197">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="f5b61-198">這是適用於測試 API 的要求使用者登入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f5b61-198">This is useful for testing API's that require the user to be signed-in with an account.</span></span> <span data-ttu-id="f5b61-199">之後核取方塊，在此頁面上後續啟動模擬器將會要求您登入，就像使用者一樣第一次啟動 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f5b61-199">After checking the box on this page, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5b61-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b61-200">See also</span></span>
* <span data-ttu-id="f5b61-201">[進階的 HoloLens 模擬器] 和 [混合實境模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)</span><span class="sxs-lookup"><span data-stu-id="f5b61-201">[Advanced HoloLens Emulator and Mixed Reality Simulator input](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)</span></span>
* [<span data-ttu-id="f5b61-202">HoloLens 模擬器軟體歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f5b61-202">HoloLens emulator software history</span></span>](hololens-emulator-archive.md)
* [<span data-ttu-id="f5b61-203">在 Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="f5b61-203">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="f5b61-204">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="f5b61-204">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
