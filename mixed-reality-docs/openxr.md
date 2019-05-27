---
title: OpenXR
description: 試試看暫時 OpenXR 0.90 API 與混合實境 OpenXR 開發人員預覽版本。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的實境 OpenXR 開發人員預覽
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039175"
---
# <a name="openxr"></a><span data-ttu-id="f462a-104">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f462a-104">OpenXR</span></span>

<span data-ttu-id="f462a-105">OpenXR 為從開放免費標準[Khronos](https://www.khronos.org/)跨越的許多廠商的各種裝置提供原生形式存取[混合的實境頻譜](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="f462a-105">OpenXR is an open royalty-free standard from [Khronos](https://www.khronos.org/) that provides native access to a wide range of devices from many vendors that span across the [mixed reality spectrum](mixed-reality.md).</span></span>

<span data-ttu-id="f462a-106">OpenXR，您可以建置全像攝影版裝置 （例如 HoloLens 2) 放置在真實世界的數位內容，就好像沒什麼，以及 （例如桌上型電腦的 Windows Mixed Reality 耳機） 隱藏的沈浸式裝置為目標的應用程式真實世界，並取代為數位體驗。</span><span class="sxs-lookup"><span data-stu-id="f462a-106">With OpenXR, you can build applications that target both holographic devices (like HoloLens 2) that place digital content in the real world as if it were really there, as well as immersive devices (like Windows Mixed Reality headsets for desktop PCs) that hide the physical world and replace it with a digital experience.</span></span>  <span data-ttu-id="f462a-107">OpenXR 可讓您撰寫程式碼完成之後再可攜式跨各種不同的硬體平台。</span><span class="sxs-lookup"><span data-stu-id="f462a-107">OpenXR lets you write code once that's then portable across a wide range of hardware platforms.</span></span>

<span data-ttu-id="f462a-108">OpenXR 標準處於目前佈建階段中，但針對意見反應所發行的初始 OpenXR 0.90 規格。</span><span class="sxs-lookup"><span data-stu-id="f462a-108">The OpenXR standard is currently in a provisional phase, with an initial OpenXR 0.90 spec released for feedback.</span></span>  <span data-ttu-id="f462a-109">如需有關 OpenXR，包括存取權[暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)並[標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，請參閱[Khronos OpenXR 頁面](https://www.khronos.org/openxr/)。</span><span class="sxs-lookup"><span data-stu-id="f462a-109">For more information on OpenXR, including access to the [provisional 0.90 spec](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) and [headers](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), see the [Khronos OpenXR page](https://www.khronos.org/openxr/).</span></span> 

<span data-ttu-id="f462a-110">您可以試試看暫時 OpenXR 0.90 API HoloLens 2 或使用混合實境 OpenXR 開發人員預覽的桌上型個人電腦上。</span><span class="sxs-lookup"><span data-stu-id="f462a-110">You can try out the provisional OpenXR 0.90 API on a HoloLens 2 or a desktop PC using the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="f462a-111">這個早期的執行階段可讓目標 OpenXR 0.90 API 的應用程式以 HoloLens 2 或 Windows Mixed Reality 沈浸式耳機在桌面為目標。</span><span class="sxs-lookup"><span data-stu-id="f462a-111">This early runtime enables applications targeting the OpenXR 0.90 API to target HoloLens 2 or Windows Mixed Reality immersive headsets on the desktop.</span></span>

<span data-ttu-id="f462a-112">如果您沒有存取權耳機，您可以改用 HoloLens 2 模擬器] 或 [Windows Mixed Reality 模擬器。</span><span class="sxs-lookup"><span data-stu-id="f462a-112">If you don't have access to a headset, you can use the HoloLens 2 Emulator or the Windows Mixed Reality Simulator instead.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a><span data-ttu-id="f462a-113">HoloLens 2 設定混合實境 OpenXR 開發人員預覽</span><span class="sxs-lookup"><span data-stu-id="f462a-113">Setting up the Mixed Reality OpenXR Developer Preview for HoloLens 2</span></span>

<span data-ttu-id="f462a-114">若要開始使用混合實境 OpenXR Developer Preview HoloLens 2 上：</span><span class="sxs-lookup"><span data-stu-id="f462a-114">To get started with the Mixed Reality OpenXR Developer Preview on HoloLens 2:</span></span>

1. <span data-ttu-id="f462a-115">設定 HoloLens 2，或遵循指示來[安裝 HoloLens 2 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="f462a-115">Set up a HoloLens 2 or follow the instructions to [install the HoloLens 2 emulator](using-the-hololens-emulator.md).</span></span>
1. <span data-ttu-id="f462a-116">啟動從裝置或模擬器中的市集應用程式，並確保所有應用程式會更新。</span><span class="sxs-lookup"><span data-stu-id="f462a-116">Launch the Store app from within the device or emulator and ensure all apps are updated.</span></span>  <span data-ttu-id="f462a-117">這將會安裝該裝置上的應用程式使用混合實境 OpenXR Developer Preview。</span><span class="sxs-lookup"><span data-stu-id="f462a-117">This will install the Mixed Reality OpenXR Developer Preview for use with apps on that device.</span></span>  <span data-ttu-id="f462a-118">如果使用模擬器，您會想要請參閱[模擬器輸入指示](using-the-hololens-emulator.md#basic-emulator-input)可協助您使用在模擬器中的市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="f462a-118">If using the emulator, you'll want to consult the [emulator input instructions](using-the-hololens-emulator.md#basic-emulator-input) to help you use the Store app within the emulator.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a><span data-ttu-id="f462a-119">設定 沉浸式桌面耳機混合實境 OpenXR 開發人員預覽</span><span class="sxs-lookup"><span data-stu-id="f462a-119">Setting up the Mixed Reality OpenXR Developer Preview for immersive desktop headsets</span></span>

<span data-ttu-id="f462a-120">若要開始使用混合實境 OpenXR 開發人員預覽的桌上型電腦上：</span><span class="sxs-lookup"><span data-stu-id="f462a-120">To get started with the Mixed Reality OpenXR Developer Preview on a desktop PC:</span></span>

1. <span data-ttu-id="f462a-121">確定您執行 Windows 10 年 10 月 2018 Update (1809) 或 Windows 10 可能 2019年更新 (1903)。</span><span class="sxs-lookup"><span data-stu-id="f462a-121">Be sure you are running the Windows 10 October 2018 Update (1809) or the Windows 10 May 2019 Update (1903).</span></span>  <span data-ttu-id="f462a-122">如果您是在舊版的 Windows 10 上，您可以升級至 2019 年使用更新[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="f462a-122">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>
1. <span data-ttu-id="f462a-123">設定 Windows Mixed Reality 耳機或遵循指示來[啟用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)。</span><span class="sxs-lookup"><span data-stu-id="f462a-123">Set up a Windows Mixed Reality headset or follow the instructions to [enable the Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span>
1. <span data-ttu-id="f462a-124">安裝[混合的實境 OpenXR 開發人員預覽的應用程式](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。</span><span class="sxs-lookup"><span data-stu-id="f462a-124">Install the [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).</span></span>  <span data-ttu-id="f462a-125">此應用程式可讓您使用 preview OpenXR 執行階段上設定 Windows 10 年 10 月 2018 Update (1809) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f462a-125">This app gets you set up with the preview OpenXR runtime on Windows 10 October 2018 Update (1809) or later.</span></span>  <span data-ttu-id="f462a-126">安裝此應用程式之後, Windows 存放區會保留的執行階段最新狀態。</span><span class="sxs-lookup"><span data-stu-id="f462a-126">After installing this app, the Windows Store will keep the runtime up to date.</span></span>
1. <span data-ttu-id="f462a-127">從 [開始] 功能表執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。</span><span class="sxs-lookup"><span data-stu-id="f462a-127">Run the Mixed Reality OpenXR Developer Preview app from the Start menu and follow the instructions to make the runtime active.</span></span>  <span data-ttu-id="f462a-128">不久之後，此應用程式可讓您探索其他 OpenXR 偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="f462a-128">Soon, this app will let you explore other OpenXR debug information as well.</span></span>

![混合的實境 OpenXR 開發人員預覽的應用程式](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a><span data-ttu-id="f462a-130">支援 Windows 10 年 10 月 2018年更新</span><span class="sxs-lookup"><span data-stu-id="f462a-130">Support for Windows 10 October 2018 Update</span></span>

<span data-ttu-id="f462a-131">如果您執行 Windows 10 2019 年更新 (1903)，並遵循上述步驟，您應該已準備好使用混合實境 OpenXR 開發人員預覽 ！</span><span class="sxs-lookup"><span data-stu-id="f462a-131">If you're running the Windows 10 May 2019 Update (1903) and followed the steps above, you should be ready to use the Mixed Reality OpenXR Developer Preview!</span></span>

<span data-ttu-id="f462a-132">如果您尚未準備好[升級您的桌上型電腦到 2019 年更新](https://www.microsoft.com/en-us/software-download/windows10)，您可以開始在 Windows 10 年 10 月 2018年更新 (1809) 遵循一個步驟：</span><span class="sxs-lookup"><span data-stu-id="f462a-132">If you're not ready to [upgrade your desktop PC to the May 2019 Update](https://www.microsoft.com/en-us/software-download/windows10), you can get going on the Windows 10 October 2018 Update (1809) by following one more step:</span></span>

1. <span data-ttu-id="f462a-133">請遵循上述步驟，以安裝混合實境 OpenXR 開發人員預覽。</span><span class="sxs-lookup"><span data-stu-id="f462a-133">Follow the steps above to install the Mixed Reality OpenXR Developer Preview.</span></span>
1. <span data-ttu-id="f462a-134">若要設定混合實境 OpenXR 開發人員預覽使用中 OpenXR 執行階段，您的系統，安裝[混合實境 OpenXR Developer Preview 相容性套件](https://aka.ms/openxr-compat)。</span><span class="sxs-lookup"><span data-stu-id="f462a-134">To set the Mixed Reality OpenXR Developer Preview as your system's active OpenXR runtime, install the [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).</span></span>

## <a name="building-a-sample-openxr-app"></a><span data-ttu-id="f462a-135">建置範例 OpenXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="f462a-135">Building a sample OpenXR app</span></span>

<span data-ttu-id="f462a-136">[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)專案會示範簡單的 OpenXR 範例使用兩個 Visual Studio 專案檔，一個同時 Win32 桌面應用程式，另一個 UWP HoloLens 2 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f462a-136">The [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) project demonstrates a simple OpenXR sample with two Visual Studio project files, one for both a Win32 desktop app and one for a UWP HoloLens 2 app.</span></span>  <span data-ttu-id="f462a-137">因為方案中包含的 HoloLens UWP 專案，您將需要[通用 Windows 平台開發工作負載](install-the-tools.md#installation-checklist)完全開啟的 Visual Studio 中安裝。</span><span class="sxs-lookup"><span data-stu-id="f462a-137">Because the solution contains a HoloLens UWP project, you'll need the [Universal Windows Platform development workload](install-the-tools.md#installation-checklist) installed in Visual Studio to fully open it.</span></span>

<span data-ttu-id="f462a-138">請注意，由於差異封裝和部署，每個專案內的應用程式程式碼個別 Win32 與 UWP 專案檔時等於 100%！</span><span class="sxs-lookup"><span data-stu-id="f462a-138">Note that while the Win32 and UWP project files are separate due to differences in packaging and deployment, the app code inside each project is 100% the same!</span></span>

## <a name="feedback"></a><span data-ttu-id="f462a-139">意見反應</span><span class="sxs-lookup"><span data-stu-id="f462a-139">Feedback</span></span>

<span data-ttu-id="f462a-140">若要提供意見反應[OpenXR 暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)而[規格問題追蹤程式](https://github.com/KhronosGroup/OpenXR-Docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="f462a-140">To give feedback on the [OpenXR Provisional 0.90 specification](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr), [Slack #openxr channel](https://khr.io/slack) and the [spec issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f462a-141">疑難排解</span><span class="sxs-lookup"><span data-stu-id="f462a-141">Troubleshooting</span></span>

<span data-ttu-id="f462a-142">以下是一些疑難排解的秘訣，混合實境 OpenXR 開發人員預覽版本。</span><span class="sxs-lookup"><span data-stu-id="f462a-142">Here are some troubleshooting tips for the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="f462a-143">如果您遇到任何其他問題，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)或是[#openxr Slack 通道](https://khr.io/slack)。</span><span class="sxs-lookup"><span data-stu-id="f462a-143">If you're hitting any other problems, please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) or [Slack #openxr channel](https://khr.io/slack).</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="f462a-144">無法啟動 Windows Mixed Reality OpenXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="f462a-144">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="f462a-145">如果 OpenXR 應用程式無法啟動程式 Windows Mixed Reality，在執行時，混合實境 OpenXR 開發人員預覽可能不設定為使用中的執行階段。</span><span class="sxs-lookup"><span data-stu-id="f462a-145">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Mixed Reality OpenXR Developer Preview may not be set as the active runtime.</span></span>  <span data-ttu-id="f462a-146">請務必先執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。</span><span class="sxs-lookup"><span data-stu-id="f462a-146">Be sure to run the Mixed Reality OpenXR Developer Preview app and follow the instructions to make the runtime active.</span></span>

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a><span data-ttu-id="f462a-147">混合的實境 OpenXR 開發人員預覽應用程式無法安裝</span><span class="sxs-lookup"><span data-stu-id="f462a-147">Mixed Reality OpenXR Developer Preview app cannot be installed</span></span> 

<span data-ttu-id="f462a-148">確定您至少執行 Windows 10 年 10 月 2018年更新 (1809)。</span><span class="sxs-lookup"><span data-stu-id="f462a-148">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="f462a-149">如果您是在舊版的 Windows 10 上，您可以升級至 2019 年更新 (1903) 使用[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="f462a-149">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="f462a-150">如果混合實境 OpenXR 開發人員預覽應用程式上的 [安裝] 按鈕不會在 Windows 上執行任何動作 10 年 10 月 2018年更新，您的系統可能已快取應用程式的過時的系統需求。</span><span class="sxs-lookup"><span data-stu-id="f462a-150">If the Install button on the Mixed Reality OpenXR Developer Preview app does nothing on Windows 10 October 2018 Update, your system may have cached stale system requirements for the app.</span></span>  <span data-ttu-id="f462a-151">您可以執行命令`wsreset.exe`清除快取的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f462a-151">You can run the command `wsreset.exe` from a command prompt to clear the cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="f462a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f462a-152">See also</span></span>

* [<span data-ttu-id="f462a-153">更多有關 OpenXR</span><span class="sxs-lookup"><span data-stu-id="f462a-153">More information on OpenXR</span></span>](https://www.khronos.org/openxr/)
* [<span data-ttu-id="f462a-154">OpenXR 暫時 0.90 規格</span><span class="sxs-lookup"><span data-stu-id="f462a-154">OpenXR Provisional 0.90 specification</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [<span data-ttu-id="f462a-155">OpenXR 暫時 0.90 API 參考</span><span class="sxs-lookup"><span data-stu-id="f462a-155">OpenXR Provisional 0.90 API reference</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [<span data-ttu-id="f462a-156">OpenXR 暫時 0.90 標頭</span><span class="sxs-lookup"><span data-stu-id="f462a-156">OpenXR Provisional 0.90 headers</span></span>](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [<span data-ttu-id="f462a-157">OpenXR 暫時 0.90 快速參考指南</span><span class="sxs-lookup"><span data-stu-id="f462a-157">OpenXR Provisional 0.90 quick reference guide</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
