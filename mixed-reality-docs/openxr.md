---
title: OpenXR
description: 試試看暫時 OpenXR 0.90 API 與混合實境 OpenXR 開發人員預覽版本。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的實境 OpenXR 開發人員預覽
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596355"
---
# <a name="openxr"></a><span data-ttu-id="adc56-104">OpenXR</span><span class="sxs-lookup"><span data-stu-id="adc56-104">OpenXR</span></span>

<span data-ttu-id="adc56-105">OpenXR 為從開放免費標準[Khronos](https://www.khronos.org/)跨越的許多廠商的各種裝置提供原生形式存取[混合的實境頻譜](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="adc56-105">OpenXR is an open royalty-free standard from [Khronos](https://www.khronos.org/) that provides native access to a wide range of devices from many vendors that span across the [mixed reality spectrum](mixed-reality.md).</span></span>

<span data-ttu-id="adc56-106">OpenXR，您可以建置全像攝影版裝置 （例如 HoloLens 2) 放置在真實世界的數位內容，就好像沒什麼，以及 （例如桌上型電腦的 Windows Mixed Reality 耳機） 隱藏的沈浸式裝置為目標的應用程式真實世界，並取代為數位體驗。</span><span class="sxs-lookup"><span data-stu-id="adc56-106">With OpenXR, you can build applications that target both holographic devices (like HoloLens 2) that place digital content in the real world as if it were really there, as well as immersive devices (like Windows Mixed Reality headsets for desktop PCs) that hide the physical world and replace it with a digital experience.</span></span>  <span data-ttu-id="adc56-107">OpenXR 可讓您撰寫程式碼完成之後再可攜式跨各種不同的硬體平台。</span><span class="sxs-lookup"><span data-stu-id="adc56-107">OpenXR lets you write code once that's then portable across a wide range of hardware platforms.</span></span>

<span data-ttu-id="adc56-108">OpenXR 標準處於目前佈建階段中，但針對意見反應所發行的初始 OpenXR 0.90 規格。</span><span class="sxs-lookup"><span data-stu-id="adc56-108">The OpenXR standard is currently in a provisional phase, with an initial OpenXR 0.90 spec released for feedback.</span></span>  <span data-ttu-id="adc56-109">如需有關 OpenXR，包括存取權[暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)並[標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，請參閱[Khronos OpenXR 頁面](https://www.khronos.org/openxr/)。</span><span class="sxs-lookup"><span data-stu-id="adc56-109">For more information on OpenXR, including access to the [provisional 0.90 spec](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) and [headers](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), see the [Khronos OpenXR page](https://www.khronos.org/openxr/).</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a><span data-ttu-id="adc56-110">設定混合實境 OpenXR 開發人員預覽</span><span class="sxs-lookup"><span data-stu-id="adc56-110">Setting up the Mixed Reality OpenXR Developer Preview</span></span>

<span data-ttu-id="adc56-111">您可以試試看今天使用混合實境 OpenXR 開發人員預覽的暫時 OpenXR 0.90 API。</span><span class="sxs-lookup"><span data-stu-id="adc56-111">You can try out the provisional OpenXR 0.90 API today using the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="adc56-112">這個早期的執行階段可讓目標在桌面上目標 Windows Mixed Reality 沈浸式耳機 OpenXR 0.90 API 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="adc56-112">This early runtime enables applications targeting the OpenXR 0.90 API to target Windows Mixed Reality immersive headsets on the desktop.</span></span>  <span data-ttu-id="adc56-113">如果您沒有存取權耳機，您可以改為使用 Windows Mixed Reality 模擬器。</span><span class="sxs-lookup"><span data-stu-id="adc56-113">If you don't have access to a headset, you can use the Windows Mixed Reality Simulator instead.</span></span>

<span data-ttu-id="adc56-114">若要開始使用混合實境 OpenXR 開發人員預覽版本：</span><span class="sxs-lookup"><span data-stu-id="adc56-114">To get started with the Mixed Reality OpenXR Developer Preview:</span></span>

1. <span data-ttu-id="adc56-115">確定您至少執行 Windows 10 年 10 月 2018年的更新。</span><span class="sxs-lookup"><span data-stu-id="adc56-115">Be sure you are running at least the Windows 10 October 2018 Update.</span></span>  <span data-ttu-id="adc56-116">如果您是在舊版的 Windows 10 上，您可以升級至 10 月 2018年更新[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="adc56-116">If you're on an earlier version of Windows 10, you can upgrade to the October 2018 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>  <span data-ttu-id="adc56-117">如果您覺得探險，您可以安裝[Windows 10 Insider Preview 組建](https://insider.windows.com)。</span><span class="sxs-lookup"><span data-stu-id="adc56-117">If you're feeling adventurous, you can install a [Windows 10 Insider Preview build](https://insider.windows.com).</span></span>
1. <span data-ttu-id="adc56-118">設定 Windows Mixed Reality 耳機或遵循指示來[啟用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)。</span><span class="sxs-lookup"><span data-stu-id="adc56-118">Set up a Windows Mixed Reality headset or follow the instructions to [enable the Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span>
1. <span data-ttu-id="adc56-119">安裝[混合的實境 OpenXR 開發人員預覽的應用程式](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。</span><span class="sxs-lookup"><span data-stu-id="adc56-119">Install the [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).</span></span>  <span data-ttu-id="adc56-120">此應用程式可讓您使用 preview OpenXR 執行階段上設定 Windows 10 年 10 月 2018年更新或更新版本。</span><span class="sxs-lookup"><span data-stu-id="adc56-120">This app gets you set up with the preview OpenXR runtime on Windows 10 October 2018 Update or later.</span></span>  <span data-ttu-id="adc56-121">安裝此應用程式之後, Windows 存放區會保留的執行階段最新狀態。</span><span class="sxs-lookup"><span data-stu-id="adc56-121">After installing this app, the Windows Store will keep the runtime up to date.</span></span>
1. <span data-ttu-id="adc56-122">從 [開始] 功能表執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。</span><span class="sxs-lookup"><span data-stu-id="adc56-122">Run the Mixed Reality OpenXR Developer Preview app from the Start menu and follow the instructions to make the runtime active.</span></span>  <span data-ttu-id="adc56-123">不久之後，此應用程式可讓您探索其他 OpenXR 偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="adc56-123">Soon, this app will let you explore other OpenXR debug information as well.</span></span>

![混合的實境 OpenXR 開發人員預覽的應用程式](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a><span data-ttu-id="adc56-125">支援 Windows 10 年 10 月 2018年更新</span><span class="sxs-lookup"><span data-stu-id="adc56-125">Support for Windows 10 October 2018 Update</span></span>

<span data-ttu-id="adc56-126">若要開始使用混合實境 OpenXR 開發人員預覽在 Windows 10 年 10 月 2018年更新 （Windows 目前版本），您必須遵循幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="adc56-126">To get going with the Mixed Reality OpenXR Developer Preview on the Windows 10 October 2018 Update (the current version of Windows), you'll need to follow a few more steps:</span></span>

1. <span data-ttu-id="adc56-127">請遵循上述步驟，以安裝混合實境 OpenXR 開發人員預覽。</span><span class="sxs-lookup"><span data-stu-id="adc56-127">Follow the steps above to install the Mixed Reality OpenXR Developer Preview.</span></span>
1. <span data-ttu-id="adc56-128">若要設定混合實境 OpenXR 開發人員預覽使用中 OpenXR 執行階段，您的系統，安裝[混合實境 OpenXR Developer Preview 相容性套件](https://aka.ms/openxr-compat)。</span><span class="sxs-lookup"><span data-stu-id="adc56-128">To set the Mixed Reality OpenXR Developer Preview as your system's active OpenXR runtime, install the [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).</span></span>

## <a name="building-a-test-openxr-app"></a><span data-ttu-id="adc56-129">建置測試 OpenXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="adc56-129">Building a test OpenXR app</span></span>

<span data-ttu-id="adc56-130">[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR 測試應用程式示範如何使用 API 的各種組件。</span><span class="sxs-lookup"><span data-stu-id="adc56-130">The [hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR test app demonstrates use of various parts of the API.</span></span>  <span data-ttu-id="adc56-131">您可以遵循這些[組建指示](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md)，這會建置測試應用程式和 OpenXR 標頭本身。</span><span class="sxs-lookup"><span data-stu-id="adc56-131">You can follow these [build instructions](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), which will build both the test app and the OpenXR headers themselves.</span></span>

## <a name="feedback"></a><span data-ttu-id="adc56-132">意見反應</span><span class="sxs-lookup"><span data-stu-id="adc56-132">Feedback</span></span>

<span data-ttu-id="adc56-133">若要提供意見反應[OpenXR 暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)而[規格問題追蹤程式](https://github.com/KhronosGroup/OpenXR-Docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="adc56-133">To give feedback on the [OpenXR Provisional 0.90 specification](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr), [Slack #openxr channel](https://khr.io/slack) and the [spec issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="adc56-134">疑難排解</span><span class="sxs-lookup"><span data-stu-id="adc56-134">Troubleshooting</span></span>

<span data-ttu-id="adc56-135">以下是一些疑難排解的秘訣，混合實境 OpenXR 開發人員預覽版本。</span><span class="sxs-lookup"><span data-stu-id="adc56-135">Here are some troubleshooting tips for the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="adc56-136">如果您遇到任何其他問題，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)或是[#openxr Slack 通道](https://khr.io/slack)。</span><span class="sxs-lookup"><span data-stu-id="adc56-136">If you're hitting any other problems, please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) or [Slack #openxr channel](https://khr.io/slack).</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="adc56-137">無法啟動 Windows Mixed Reality OpenXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="adc56-137">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="adc56-138">如果 OpenXR 應用程式無法啟動程式 Windows Mixed Reality，在執行時，混合實境 OpenXR 開發人員預覽可能不設定為使用中的執行階段。</span><span class="sxs-lookup"><span data-stu-id="adc56-138">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Mixed Reality OpenXR Developer Preview may not be set as the active runtime.</span></span>  <span data-ttu-id="adc56-139">請務必先執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。</span><span class="sxs-lookup"><span data-stu-id="adc56-139">Be sure to run the Mixed Reality OpenXR Developer Preview app and follow the instructions to make the runtime active.</span></span>

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a><span data-ttu-id="adc56-140">混合的實境 OpenXR 開發人員預覽應用程式無法安裝</span><span class="sxs-lookup"><span data-stu-id="adc56-140">Mixed Reality OpenXR Developer Preview app cannot be installed</span></span> 

<span data-ttu-id="adc56-141">確定您至少執行 Windows 10 年 10 月 2018年的更新。</span><span class="sxs-lookup"><span data-stu-id="adc56-141">Be sure you are running at least the Windows 10 October 2018 Update.</span></span>  <span data-ttu-id="adc56-142">如果您是在舊版的 Windows 10 上，您可以升級至 10 月 2018年更新[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="adc56-142">If you're on an earlier version of Windows 10, you can upgrade to the October 2018 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="adc56-143">如果混合實境 OpenXR 開發人員預覽應用程式上的 [安裝] 按鈕不會在 Windows 上執行任何動作 10 年 10 月 2018年更新，您的系統可能已快取應用程式的過時的系統需求。</span><span class="sxs-lookup"><span data-stu-id="adc56-143">If the Install button on the Mixed Reality OpenXR Developer Preview app does nothing on Windows 10 October 2018 Update, your system may have cached stale system requirements for the app.</span></span>  <span data-ttu-id="adc56-144">您可以執行命令`wsreset.exe`清除快取的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="adc56-144">You can run the command `wsreset.exe` from a command prompt to clear the cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="adc56-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc56-145">See also</span></span>

* [<span data-ttu-id="adc56-146">更多有關 OpenXR</span><span class="sxs-lookup"><span data-stu-id="adc56-146">More information on OpenXR</span></span>](https://www.khronos.org/openxr/)
* [<span data-ttu-id="adc56-147">OpenXR 暫時 0.90 規格</span><span class="sxs-lookup"><span data-stu-id="adc56-147">OpenXR Provisional 0.90 specification</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [<span data-ttu-id="adc56-148">OpenXR 暫時 0.90 API 參考</span><span class="sxs-lookup"><span data-stu-id="adc56-148">OpenXR Provisional 0.90 API reference</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [<span data-ttu-id="adc56-149">OpenXR 暫時 0.90 標頭</span><span class="sxs-lookup"><span data-stu-id="adc56-149">OpenXR Provisional 0.90 headers</span></span>](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
