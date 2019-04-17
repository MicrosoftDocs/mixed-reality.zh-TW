---
title: 更新混合實境的 2D UWP 應用的程式
description: 本文章概述更新您現有 2D 通用 Windows 平台應用程式上執行 HoloLens 與 Windows Mixed Reality 沈浸式耳機。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式，UWP，一般應用程式、 HoloLens、 沈浸式耳機，應用程式模型後按鈕、 應用程式列、 dpi、 解析，小數位數
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595365"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a><span data-ttu-id="08816-104">更新混合實境的 2D UWP 應用的程式</span><span class="sxs-lookup"><span data-stu-id="08816-104">Updating 2D UWP apps for mixed reality</span></span>

<span data-ttu-id="08816-105">Windows Mixed Reality 可讓使用者查看全像投影，如同它們是右周圍，在您的實體或數位世界。</span><span class="sxs-lookup"><span data-stu-id="08816-105">Windows Mixed Reality enables a user to see holograms as if they are right around you, in your physical or digital world.</span></span> <span data-ttu-id="08816-106">基本上，HoloLens 和附加沈浸式耳機附屬應用程式，可在桌面電腦是 Windows 10 裝置;這表示您能夠為 2D 應用程式存放區中執行幾乎所有的通用 Windows 平台 (UWP) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-106">At its core, both HoloLens and the Desktop PCs you attach immersive headset accessories to are Windows 10 devices; this means that you're able to run almost all of the Universal Windows Platform (UWP) apps in the Store as 2D apps.</span></span>

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a><span data-ttu-id="08816-107">建立混合實境的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-107">Creating a 2D UWP app for mixed reality</span></span>

<span data-ttu-id="08816-108">2D 應用程式帶入混合的實境耳機的第一個步驟是取得您以標準 2D 應用程式在桌面的監視器上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-108">The first step to bringing a 2D app to mixed reality headsets is to get your app running as a standard 2D app on your desktop monitor.</span></span>

### <a name="building-a-new-2d-uwp-app"></a><span data-ttu-id="08816-109">建立新的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-109">Building a new 2D UWP app</span></span>

<span data-ttu-id="08816-110">若要建立新的混合實境 2D 應用程式，您只需建置標準的 2D 通用 Windows 平台 (UWP) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-110">To build a new 2D app for mixed reality, you simply build a standard 2D Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="08816-111">接著再執行在混合實境中的 靜態圖像為該應用程式需要任何其他應用程式變更不。</span><span class="sxs-lookup"><span data-stu-id="08816-111">No other app changes are required for that app to then run as a slate in mixed reality.</span></span>

<span data-ttu-id="08816-112">若要開始建置 2D 的 UWP 應用程式，請參閱[建立第一個應用程式](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文章。</span><span class="sxs-lookup"><span data-stu-id="08816-112">To get started building a 2D UWP app, check out the [Create your first app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) article.</span></span>

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a><span data-ttu-id="08816-113">將現有的 2D 市集應用程式帶到 UWP</span><span class="sxs-lookup"><span data-stu-id="08816-113">Bringing an existing 2D Store app to UWP</span></span>

<span data-ttu-id="08816-114">如果您已經有 2D 的 Windows 應用程式存放區中，您必須先確定它設為目標 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="08816-114">If you already have a 2D Windows app in the Store, you must first ensure it is targeting the Windows 10 Universal Windows Platform (UWP).</span></span> <span data-ttu-id="08816-115">以下是所有可能起始點您可能與您的市集應用程式立即：</span><span class="sxs-lookup"><span data-stu-id="08816-115">Here are all the potential starting points you may have with your Store app today:</span></span>
<br>

|  <span data-ttu-id="08816-116">起點</span><span class="sxs-lookup"><span data-stu-id="08816-116">Starting Point</span></span>  |  <span data-ttu-id="08816-117">AppX 資訊清單平台目標</span><span class="sxs-lookup"><span data-stu-id="08816-117">AppX Manifest Platform Target</span></span>  |  <span data-ttu-id="08816-118">若要使此通用如何？</span><span class="sxs-lookup"><span data-stu-id="08816-118">How to make this Universal?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="08816-119">Windows Phone (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="08816-119">Windows Phone (Silverlight)</span></span>  |  <span data-ttu-id="08816-120">Silverlight 應用程式資訊清單</span><span class="sxs-lookup"><span data-stu-id="08816-120">Silverlight App Manifest</span></span> |  <span data-ttu-id="08816-121">[將移轉到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="08816-121">[Migrate to WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span></span> | 
|  <span data-ttu-id="08816-122">Windows Phone 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="08816-122">Windows Phone 8.1 Universal</span></span>  |  <span data-ttu-id="08816-123">8.1 AppX 資訊清單不包含平台目標</span><span class="sxs-lookup"><span data-stu-id="08816-123">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="08816-124">將您的應用程式移轉至通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="08816-124">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="08816-125">Windows 市集 8</span><span class="sxs-lookup"><span data-stu-id="08816-125">Windows Store 8</span></span>  |  <span data-ttu-id="08816-126">8 AppX 資訊清單不包含平台目標</span><span class="sxs-lookup"><span data-stu-id="08816-126">8 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="08816-127">將您的應用程式移轉至通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="08816-127">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="08816-128">Windows 市集 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="08816-128">Windows Store 8.1 Universal</span></span>  |  <span data-ttu-id="08816-129">8.1 AppX 資訊清單不包含平台目標</span><span class="sxs-lookup"><span data-stu-id="08816-129">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="08816-130">將您的應用程式移轉至通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="08816-130">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 

<span data-ttu-id="08816-131">如果您有立即建置 Win32 應用程式 （"PC、 Mac 和 Linux 單機版 」 組建目標） 為 2D Unity 應用程式時，您可以針對混合的實境，改為切換到 「 通用 Windows 平台 」 建置目標的 Unity。</span><span class="sxs-lookup"><span data-stu-id="08816-131">If you have a 2D Unity app today built as a Win32 app (the "PC, Mac & Linux Standalone" build target), you can target mixed reality by switching Unity to the "Universal Windows Platform" build target instead.</span></span>

<span data-ttu-id="08816-132">我們將討論方式，您可以限制您的應用程式是專為使用 Windows.Holographic 裝置家族的 HoloLens[以下](#publish-and-maintain-your-universal-app)。</span><span class="sxs-lookup"><span data-stu-id="08816-132">We'll talk about ways that you can restrict your app specifically to HoloLens using the Windows.Holographic device family [below](#publish-and-maintain-your-universal-app).</span></span>

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a><span data-ttu-id="08816-133">執行 Windows Mixed Reality 沈浸式耳機 2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-133">Run your 2D app in a Windows Mixed Reality immersive headset</span></span>

<span data-ttu-id="08816-134">如果您正在開發並試用您的監視器上桌上型電腦部署了 2D 應用程式之後，您已經準備好要試試看在沉浸式桌面耳機 ！</span><span class="sxs-lookup"><span data-stu-id="08816-134">If you've deployed your 2D app to the desktop machine where you are developing and tried it out on your monitor, you're already ready to try it out in an immersive desktop headset!</span></span>

<span data-ttu-id="08816-135">只要移至混合的實境耳機內的 [開始] 功能表，然後啟動應用程式，從該處。</span><span class="sxs-lookup"><span data-stu-id="08816-135">Just go to the Start menu within the mixed reality headset and launch the app from there.</span></span> <span data-ttu-id="08816-136">桌面殼層和全像攝影版的殼層都共用相同一組的 UWP 應用程式，並因此應用程式應該會出現，一旦您從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="08816-136">The desktop shell and the holographic shell both share the same set of UWP apps, and so the app should already be present once you've deployed from Visual Studio.</span></span>

## <a name="targeting-both-immersive-headsets-and-hololens"></a><span data-ttu-id="08816-137">為目標的沈浸式耳機和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="08816-137">Targeting both immersive headsets and HoloLens</span></span>

<span data-ttu-id="08816-138">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="08816-138">Congratulations!</span></span> <span data-ttu-id="08816-139">您的應用程式正在使用 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="08816-139">Your app is now using the Windows 10 Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="08816-140">現在能在現今的 Windows 裝置，例如桌面、 行動、 Windows Mixed Reality 沈浸式耳機的 Xbox 和 HoloLens，以及為未來的 Windows 裝置上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-140">Your app is now capable of running on today's Windows devices like Desktop, Mobile, Xbox, Windows Mixed Reality immersive headsets, and HoloLens, as well as future Windows devices.</span></span> <span data-ttu-id="08816-141">不過，若要實際目標的所有這些裝置，您必須確保您的應用程式的目標 Windows.Universal 裝置系列。</span><span class="sxs-lookup"><span data-stu-id="08816-141">However, to actually target all of those devices, you will need to ensure your app is targeting the Windows.Universal device family.</span></span>

### <a name="change-your-device-family-to-windowsuniversal"></a><span data-ttu-id="08816-142">將您的裝置系列變更為 Windows.Universal</span><span class="sxs-lookup"><span data-stu-id="08816-142">Change your device family to Windows.Universal</span></span>

<span data-ttu-id="08816-143">現在讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以執行 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="08816-143">Now let's jump into your AppX manifest to ensure your Windows 10 UWP app can run on HoloLens:</span></span>
* <span data-ttu-id="08816-144">開啟您的應用程式使用的方案檔**Visual Studio**並瀏覽至應用程式封裝資訊清單</span><span class="sxs-lookup"><span data-stu-id="08816-144">Open your app's solution file with **Visual Studio** and navigate to the app package manifest</span></span>
* <span data-ttu-id="08816-145">以滑鼠右鍵按一下**Package.appxmanifest**檔案中您的解決方案，並移至**檢視程式碼**</span><span class="sxs-lookup"><span data-stu-id="08816-145">Right click the **Package.appxmanifest** file in your Solution and go to **View Code**</span></span><br>
  <span data-ttu-id="08816-146">![在 [方案總管] 中的 package.appxmanifest](images/openappxmanifest-500px.png)</span><span class="sxs-lookup"><span data-stu-id="08816-146">![package.appxmanifest in Solution Explorer](images/openappxmanifest-500px.png)</span></span><br>
* <span data-ttu-id="08816-147">請確定您的目標平台 Windows.Universal 相依性一節</span><span class="sxs-lookup"><span data-stu-id="08816-147">Ensure your Target Platform is Windows.Universal in the dependencies section</span></span>
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* <span data-ttu-id="08816-148">儲存 ！</span><span class="sxs-lookup"><span data-stu-id="08816-148">Save!</span></span>

<span data-ttu-id="08816-149">如果您不使用 Visual Studio 開發環境，您可以開啟**AppXManifest.xml**在您的選擇，以確保您設為目標的文字編輯器**Windows.Universal** *TargetDeviceFamily*。</span><span class="sxs-lookup"><span data-stu-id="08816-149">If you do not use Visual Studio for your development environment, you can open **AppXManifest.xml** in the text editor of your choice to ensure you're targeting the **Windows.Universal** *TargetDeviceFamily*.</span></span>

### <a name="run-in-the-hololens-emulator"></a><span data-ttu-id="08816-150">HoloLens 模擬器中執行</span><span class="sxs-lookup"><span data-stu-id="08816-150">Run in the HoloLens Emulator</span></span>

<span data-ttu-id="08816-151">現在，您的 UWP 應用程式目標設為"Windows.Universal"，讓我們來建置您的應用程式，並在執行[HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="08816-151">Now that your UWP app targets "Windows.Universal", let's build your app and run it in the [HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
* <span data-ttu-id="08816-152">請確定您已[安裝 HoloLens 模擬器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="08816-152">Make sure you have [installed the HoloLens Emulator](install-the-tools.md).</span></span>
* <span data-ttu-id="08816-153">在 Visual Studio 中，選取**x86**建置您的應用程式的組態</span><span class="sxs-lookup"><span data-stu-id="08816-153">In Visual Studio, select the **x86** build configuration for your app</span></span>

  ![x86 建置在 Visual Studio 中的組態](images/x86setting.png)<br>
* <span data-ttu-id="08816-155">選取  **HoloLens 模擬器**部署目標下拉式選單中</span><span class="sxs-lookup"><span data-stu-id="08816-155">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span>

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* <span data-ttu-id="08816-157">選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="08816-157">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="08816-158">模擬器會啟動，並執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-158">The emulator will start and run your app.</span></span>
* <span data-ttu-id="08816-159">使用鍵盤、 滑鼠及/或 Xbox 控制器，會將您應用程式世界各地的啟動它。</span><span class="sxs-lookup"><span data-stu-id="08816-159">With a keyboard, mouse, and/or an Xbox controller, place your app in the world to launch it.</span></span>

  ![HoloLens 模擬器載入 UWP 範例](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a><span data-ttu-id="08816-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="08816-161">Next steps</span></span>

<span data-ttu-id="08816-162">此時，會發生下列其中一種：</span><span class="sxs-lookup"><span data-stu-id="08816-162">At this point, one of two things can happen:</span></span>
1. <span data-ttu-id="08816-163">您的應用程式會顯示其開頭顯示畫面，並啟動之後它會放在模擬器中執行 ！</span><span class="sxs-lookup"><span data-stu-id="08816-163">Your app will show its splash and start running after it is placed in the Emulator!</span></span> <span data-ttu-id="08816-164">好極了 ！</span><span class="sxs-lookup"><span data-stu-id="08816-164">Awesome!</span></span>
2. <span data-ttu-id="08816-165">或者，您會看到如 2D 全像載入的動畫後，載入將會停止，而且您將只會看到您的應用程式在其啟動顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="08816-165">Or after you see a loading animation for a 2D hologram, loading will stop and you will just see your app at its splash screen.</span></span> <span data-ttu-id="08816-166">這表示發生錯誤，而且需要更多的調查，以了解如何在混合實境中實現您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-166">This means that something went wrong and it will take more investigation to understand how to bring your app to life in Mixed Reality.</span></span>

<span data-ttu-id="08816-167">若要取得的功能可能會導致您的 UWP 應用程式底部不 HoloLens 上啟動，您必須偵錯。</span><span class="sxs-lookup"><span data-stu-id="08816-167">To get to the bottom of what may be causing your UWP app not to start on HoloLens, you'll have to debug.</span></span>

### <a name="running-your-uwp-app-in-the-debugger"></a><span data-ttu-id="08816-168">在 偵錯工具中執行您的 UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-168">Running your UWP app in the debugger</span></span>

<span data-ttu-id="08816-169">這些步驟將引導您使用 Visual Studio 偵錯工具的 UWP 應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="08816-169">These steps will walk you through debugging your UWP app using the Visual Studio debugger.</span></span>
* <span data-ttu-id="08816-170">如果您尚未這麼做，請在 Visual Studio 中開啟的方案。</span><span class="sxs-lookup"><span data-stu-id="08816-170">If you haven't already done so, open your solution in Visual Studio.</span></span> <span data-ttu-id="08816-171">變更目標，以便**HoloLens 模擬器**和 組建組態設為**x86**。</span><span class="sxs-lookup"><span data-stu-id="08816-171">Change the target to the **HoloLens Emulator** and the build configuration to **x86**.</span></span>
* <span data-ttu-id="08816-172">選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="08816-172">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="08816-173">使用您的滑鼠、 鍵盤或 Xbox 控制器世界中的應用程式的地方。</span><span class="sxs-lookup"><span data-stu-id="08816-173">Place the app in the world with your mouse, keyboard, or Xbox controller.</span></span>
* <span data-ttu-id="08816-174">Visual Studio 現在應該在應用程式程式碼中某處中斷。</span><span class="sxs-lookup"><span data-stu-id="08816-174">Visual Studio should now break somewhere in your app code.</span></span>
  - <span data-ttu-id="08816-175">如果您的應用程式不會立即損毀，或偵錯工具中斷，因為發生未處理的錯誤，然後瀏覽您的應用程式，以確定一切都運作和功能的核心功能測試。</span><span class="sxs-lookup"><span data-stu-id="08816-175">If your app doesn't immediately crash or break into the debugger because of an unhandled error, then go through a test pass of the core features of your app to make sure everything is running and functional.</span></span> <span data-ttu-id="08816-176">您可能會看到錯誤，例如圖 （內部例外狀況處理）。</span><span class="sxs-lookup"><span data-stu-id="08816-176">You may see errors like pictured below (internal exceptions that are being handled).</span></span> <span data-ttu-id="08816-177">若要確保您千萬別錯過影響您的應用程式體驗的內部錯誤，執行您的自動化的測試和單元測試，藉此確定一切如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="08816-177">To ensure you don't miss internal errors that impact the experience of your app, run through your automated tests and unit tests to make sure everything behaves as expected.</span></span>

![HoloLens 模擬器載入 UWP 範例顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a><span data-ttu-id="08816-179">更新您的 UI</span><span class="sxs-lookup"><span data-stu-id="08816-179">Update your UI</span></span>

<span data-ttu-id="08816-180">現在，您的 UWP 應用程式沈浸式耳機和/或為 2D 雷射 HoloLens 上執行，接下來我們要確定它看起來美觀。</span><span class="sxs-lookup"><span data-stu-id="08816-180">Now that your UWP app is running on immersive headsets and/or HoloLens as a 2D hologram, next we'll make sure it looks beautiful.</span></span> <span data-ttu-id="08816-181">以下是一些考量事項：</span><span class="sxs-lookup"><span data-stu-id="08816-181">Here are some things to consider:</span></span>
* <span data-ttu-id="08816-182">Windows Mixed Reality 會在固定的解析度和 DPI，等同於執行所有的 2D 應用程式以 853 x 480 有效的像素。</span><span class="sxs-lookup"><span data-stu-id="08816-182">Windows Mixed Reality will run all 2D apps at a fixed resolution and DPI that equates to 853x480 effective pixels.</span></span> <span data-ttu-id="08816-183">請考慮您的設計是否需要以這個規模調整，並檢閱設計指導方針，以改善您 HoloLens 和沈浸式耳機的體驗。</span><span class="sxs-lookup"><span data-stu-id="08816-183">Consider if your design needs refinement at this scale and review the design guidance below to improve your experience on HoloLens and immersive headsets.</span></span>
* <span data-ttu-id="08816-184">Windows Mixed Reality[不支援](app-model.md)2D 的動態磚。</span><span class="sxs-lookup"><span data-stu-id="08816-184">Windows Mixed Reality [does not support](app-model.md) 2D live tiles.</span></span> <span data-ttu-id="08816-185">如果您的核心功能顯示之動態磚的相關資訊，請考慮將該資訊移回至應用程式，或瀏覽[3D 應用程式啟動器](3d-app-launcher-design-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="08816-185">If your core functionality is showing information on a live tile, consider moving that information back into your app or explore [3D app launchers](3d-app-launcher-design-guidance.md).</span></span>

### <a name="2d-app-view-resolution-and-scale-factor"></a><span data-ttu-id="08816-186">2D 應用程式檢視解析度和比例因素</span><span class="sxs-lookup"><span data-stu-id="08816-186">2D app view resolution and scale factor</span></span>

![從 回應式設計](images/scale-500px.png)

<span data-ttu-id="08816-188">Windows 10 從實際螢幕像素為單位來移動所有視覺效果的設計**有效的像素**。</span><span class="sxs-lookup"><span data-stu-id="08816-188">Windows 10 moves all visual design from real screen pixels to **effective pixels**.</span></span> <span data-ttu-id="08816-189">這表示，開發人員設計的 Windows 10 人性化介面指導方針的有效的像素為單位，其 UI 和 Windows 調整這些有效的像素是正確的大小可確保裝置、 裝置解析度、 DPI、 使用性等等。請參閱此[MSDN 上的絕佳讀取](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)若要了解更多，以及這[組建簡報](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。</span><span class="sxs-lookup"><span data-stu-id="08816-189">That means, developers design their UI following the Windows 10 Human Interface Guidelines for effective pixels, and Windows scaling ensures those effective pixels are the right size for usability across devices, resolutions, DPI, etc. See this [great read on MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) to learn more as well as this [BUILD presentation](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).</span></span>

<span data-ttu-id="08816-190">即使有獨特的功能的應用程式放在您的世界裡，在一連串的距離，以產生最佳的可讀性和視線/手勢互動建議電視類似檢視的距離。</span><span class="sxs-lookup"><span data-stu-id="08816-190">Even with the unique ability to place apps in your world at a range of distances, TV-like viewing distances are recommended to produce the best readability and interaction with gaze/gesture.</span></span> <span data-ttu-id="08816-191">因此，混合實境在家中的虛擬 slate 將會顯示您在一般的 UWP 檢視：</span><span class="sxs-lookup"><span data-stu-id="08816-191">Because of that, a virtual slate in the Mixed Reality Home will display your flat UWP view at:</span></span>

<span data-ttu-id="08816-192">**1280 x 720，150 %dpi** （853 x 480 有效的像素）</span><span class="sxs-lookup"><span data-stu-id="08816-192">**1280x720, 150%DPI** (853x480 effective pixels)</span></span>

<span data-ttu-id="08816-193">這個解決方案有下列優點：</span><span class="sxs-lookup"><span data-stu-id="08816-193">This resolution has several advantages:</span></span>
* <span data-ttu-id="08816-194">此配置命名為有效的像素會有相關的平板電腦或小型的桌面為相同的資訊密度。</span><span class="sxs-lookup"><span data-stu-id="08816-194">This effective pixel layout will have about the same information density as a tablet or small desktop.</span></span>
* <span data-ttu-id="08816-195">它符合固定的 DPI 和 Xbox One 上，啟用順暢的體驗，在裝置上執行的 UWP 應用程式的有效像素。</span><span class="sxs-lookup"><span data-stu-id="08816-195">It matches the fixed DPI and effective pixels for UWP apps running on Xbox One, enabling seamless experiences across devices.</span></span>
* <span data-ttu-id="08816-196">此大小看起來沒問題，當我們的營運的世界中的應用程式的距離範圍擴及相應的。</span><span class="sxs-lookup"><span data-stu-id="08816-196">This size looks good when scaled across our range of operating distances for apps in the world.</span></span>

### <a name="2d-app-view-interface-design-best-practices"></a><span data-ttu-id="08816-197">2D 應用程式檢視介面設計最佳作法</span><span class="sxs-lookup"><span data-stu-id="08816-197">2D app view interface design best practices</span></span>

<span data-ttu-id="08816-198">**執行動作：**</span><span class="sxs-lookup"><span data-stu-id="08816-198">**Do:**</span></span>
* <span data-ttu-id="08816-199">請遵循[Windows 10 人性化介面指導方針 (HIG)](https://dev.windows.com/design)樣式、 字型大小和按鈕大小。</span><span class="sxs-lookup"><span data-stu-id="08816-199">Follow the [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) for styles, font sizes and button sizes.</span></span> <span data-ttu-id="08816-200">HoloLens 會執行工作，以確保您的應用程式會有相容的應用程式模式，可讀取的文字大小，以及適當的叫用的目標調整大小。</span><span class="sxs-lookup"><span data-stu-id="08816-200">HoloLens will do the work to ensure your app will have compatible app patterns, readable text sizes, and appropriate hit target sizing.</span></span>
* <span data-ttu-id="08816-201">確保您的 UI 遵循的最佳作法[回應式設計](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)尋找最佳 HoloLen 的唯一的解析度和 DPI。</span><span class="sxs-lookup"><span data-stu-id="08816-201">Ensure your UI follows best practices for [responsive design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) to look best at HoloLen's unique resolution and DPI.</span></span>
* <span data-ttu-id="08816-202">從 Windows 使用的"light"色彩佈景主題的建議。</span><span class="sxs-lookup"><span data-stu-id="08816-202">Use the "light" color theme recommendations from Windows.</span></span>

<span data-ttu-id="08816-203">**沒有此項目：**</span><span class="sxs-lookup"><span data-stu-id="08816-203">**Don't:**</span></span>
* <span data-ttu-id="08816-204">在混合實境，以確保使用者擁有流入和流出耳機熟悉的體驗也大幅變更您的 UI。</span><span class="sxs-lookup"><span data-stu-id="08816-204">Change your UI too drastically when in mixed reality, to ensure users have a familiar experience in and out of the headset.</span></span>

### <a name="understand-the-app-model"></a><span data-ttu-id="08816-205">了解應用程式模型</span><span class="sxs-lookup"><span data-stu-id="08816-205">Understand the app model</span></span>

<span data-ttu-id="08816-206">[應用程式模型](app-model.md)的混合的實境旨在使用混合實境首頁，許多應用程式一起存放的位置。</span><span class="sxs-lookup"><span data-stu-id="08816-206">The [app model](app-model.md) for mixed reality is designed to use the Mixed Reality Home, where many apps live together.</span></span> <span data-ttu-id="08816-207">把這個想成在桌面對混合的實境等項目在您執行許多的 2D 應用程式一次。</span><span class="sxs-lookup"><span data-stu-id="08816-207">Think of this as the mixed reality equivalent of the desktop, where you run many 2D apps at once.</span></span> <span data-ttu-id="08816-208">這會影響應用程式生命週期、 圖格和其他重要的功能，您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08816-208">This has implications on app life cycle, Tiles, and other key features of your app.</span></span>

### <a name="app-bar-and-back-button"></a><span data-ttu-id="08816-209">應用程式列和上一步按鈕</span><span class="sxs-lookup"><span data-stu-id="08816-209">App bar and back button</span></span>

<span data-ttu-id="08816-210">2D 檢視會附有應用程式列中，其內容上方。</span><span class="sxs-lookup"><span data-stu-id="08816-210">2D views are decorated with a app bar above their content.</span></span> <span data-ttu-id="08816-211">應用程式列中有兩個點的應用程式專屬的個人化：</span><span class="sxs-lookup"><span data-stu-id="08816-211">The app bar has two points of app-specific personalization:</span></span>

<span data-ttu-id="08816-212">**標題︰** 會顯示*displayname*應用程式執行個體相關聯的圖格</span><span class="sxs-lookup"><span data-stu-id="08816-212">**Title:** displays the *displayname* of the Tile associated with the app instance</span></span>

<span data-ttu-id="08816-213">**上一頁按鈕：** 引發*[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 時按下的事件。</span><span class="sxs-lookup"><span data-stu-id="08816-213">**Back Button:** raises the *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* event when pressed.</span></span> <span data-ttu-id="08816-214">上一步 按鈕的可見性會受到 *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*。</span><span class="sxs-lookup"><span data-stu-id="08816-214">Back Button visibility is controlled by *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.</span></span>

<span data-ttu-id="08816-215">![應用程式列在 2D 應用程式檢視中的 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="08816-215">![App bar UI in 2D app view](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span></span><br>
<span data-ttu-id="08816-216">*應用程式列在 2D 應用程式檢視中的 UI*</span><span class="sxs-lookup"><span data-stu-id="08816-216">*App bar UI in 2D app view*</span></span>

### <a name="test-your-2d-apps-design"></a><span data-ttu-id="08816-217">測試 2D 應用程式的設計</span><span class="sxs-lookup"><span data-stu-id="08816-217">Test your 2D app's design</span></span>

<span data-ttu-id="08816-218">請務必測試您的應用程式，請確定所讀取的文字、 按鈕會將目標設為，而且將整體應用程式看起來正確無誤。</span><span class="sxs-lookup"><span data-stu-id="08816-218">It is important to test your app to make sure the text is readable, the buttons are targetable, and the overall app looks correct.</span></span> <span data-ttu-id="08816-219">您可以[測試](testing-your-app-on-hololens.md)桌面耳機、 HoloLens、 模擬器，或觸控裝置解析度設定為 1280 x 720 @150%。</span><span class="sxs-lookup"><span data-stu-id="08816-219">You can [test](testing-your-app-on-hololens.md) on a desktop headset, a HoloLens, an emulator, or a touch device with resolution set to 1280x720 @150%.</span></span>

## <a name="new-input-possibilities"></a><span data-ttu-id="08816-220">新輸入的可能性</span><span class="sxs-lookup"><span data-stu-id="08816-220">New input possibilities</span></span>

<span data-ttu-id="08816-221">HoloLens 使用進階的深度感應器看到世界與使用者。</span><span class="sxs-lookup"><span data-stu-id="08816-221">HoloLens uses advanced depth sensors to see the world and see users.</span></span> <span data-ttu-id="08816-222">這可讓進階等手勢[bloom](gestures.md#bloom)並[空中點選](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="08816-222">This enables advanced hand gestures like [bloom](gestures.md#bloom) and [air-tap](gestures.md#air-tap).</span></span> <span data-ttu-id="08816-223">功能強大的麥克風也可讓[語音體驗](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="08816-223">Powerful microphones also enable [voice experiences](voice-input.md).</span></span>

<span data-ttu-id="08816-224">桌面耳機，使用者可以使用動作控制站來指向應用程式，並採取行動。</span><span class="sxs-lookup"><span data-stu-id="08816-224">With Desktop headsets, users can use motion controllers to point at apps and take action.</span></span> <span data-ttu-id="08816-225">他們也可以使用遊戲台，以其視線物件為目標。</span><span class="sxs-lookup"><span data-stu-id="08816-225">They can also use a gamepad, targeting objects with their gaze.</span></span>

<span data-ttu-id="08816-226">Windows 會負責針對 UWP 應用程式，此複雜度完全轉譯您[視線](gaze.md)，筆勢，語音和動作的輸入控制器[指標事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)，抽離輸入的機制。</span><span class="sxs-lookup"><span data-stu-id="08816-226">Windows takes care of all of this complexity for UWP apps, translating your [gaze](gaze.md), gestures, voice and motion controller input to [pointer events](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) that abstract away the input mechanism.</span></span> <span data-ttu-id="08816-227">例如，使用者可能已完成其手空中點選或提取動作控制站上的 選取的觸發程序但 2D 應用程式不需要知道其中輸入來自-他們只看到 2D 觸控按下時，如同觸控螢幕上的功能。</span><span class="sxs-lookup"><span data-stu-id="08816-227">For example, a user may have done an air-tap with their hand or pulled the Select trigger on a motion controller, but 2D applications don't need to know where the input came from - they just see a 2D touch press, as if on a touchscreen.</span></span>

<span data-ttu-id="08816-228">以下是高階概念/案例 HoloLens 將您的 UWP 應用程式時，您應該瞭解的輸入：</span><span class="sxs-lookup"><span data-stu-id="08816-228">Here are the high level concepts/scenarios you should understand for input when bringing your UWP app to HoloLens:</span></span>
* <span data-ttu-id="08816-229">[視線](gaze.md)變成暫留時的事件，非預期地觸發功能表、 延伸顯示或只要 gazing 您應用程式周圍彈出其他使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="08816-229">[Gaze](gaze.md) turns into hover events, which can unexpectedly trigger menus, flyouts or other user interface elements to pop up just by gazing around your app.</span></span>
* <span data-ttu-id="08816-230">視線不精確度可達滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="08816-230">Gaze is not as precise as mouse input.</span></span> <span data-ttu-id="08816-231">使用適當地調整大小的 HoloLens，類似且方便觸控的行動裝置應用程式，叫用的目標。</span><span class="sxs-lookup"><span data-stu-id="08816-231">Use appropriately sized hit targets for HoloLens, similar to touch-friendly mobile applications.</span></span> <span data-ttu-id="08816-232">應用程式的邊緣附近的小項目會特別難互動。</span><span class="sxs-lookup"><span data-stu-id="08816-232">Small elements near the edges of the app are especially hard to interact with.</span></span>
* <span data-ttu-id="08816-233">使用者必須切換向下捲動到拖曳兩個手指移動瀏覽至從輸入的模式。</span><span class="sxs-lookup"><span data-stu-id="08816-233">Users must switch input modes to go from scrolling to dragging to two finger panning.</span></span> <span data-ttu-id="08816-234">如果您的應用程式專為具備觸控輸入，請考慮確保任何重大的功能已被鎖定，後面兩個手指移動瀏覽。</span><span class="sxs-lookup"><span data-stu-id="08816-234">If your app was designed for touch input, consider ensuring that no major functionality is locked behind two finger panning.</span></span> <span data-ttu-id="08816-235">如果是的話，請考慮讓替代的輸入的機制，例如可以初始化兩個手指移動瀏覽 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08816-235">If so, consider having alternative input mechanisms like buttons that can initiate two finger panning.</span></span> <span data-ttu-id="08816-236">比方說，對應應用程式可以使用兩個手指移動瀏覽顯示比例，但可以加號，減號，而且旋轉來模擬相同縮放互動單一按下滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="08816-236">For example, the Maps app can zoom with two finger panning but has a plus, minus, and rotate button to simulate the same zoom interactions with single clicks.</span></span>

<span data-ttu-id="08816-237">[語音輸入](voice-input.md)是混合的實境體驗不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="08816-237">[Voice input](voice-input.md) is a critical part of the mixed reality experience.</span></span> <span data-ttu-id="08816-238">我們已啟用所有的語音使用耳機時加強 Cortana 的 Windows 10 中的 Api。</span><span class="sxs-lookup"><span data-stu-id="08816-238">We've enabled all of the speech APIs that are in Windows 10 powering Cortana when using a headset.</span></span>

## <a name="publish-and-maintain-your-universal-app"></a><span data-ttu-id="08816-239">發行及維護您的通用應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-239">Publish and Maintain your Universal app</span></span>

<span data-ttu-id="08816-240">您的應用程式啟動並執行之後，封裝您的應用程式[將它提交至 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。</span><span class="sxs-lookup"><span data-stu-id="08816-240">Once your app is up and running, package your app to [submit it to the Microsoft Store](submitting-an-app-to-the-microsoft-store.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08816-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08816-241">See also</span></span>
* [<span data-ttu-id="08816-242">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="08816-242">App model</span></span>](app-model.md)
* [<span data-ttu-id="08816-243">Gaze</span><span class="sxs-lookup"><span data-stu-id="08816-243">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="08816-244">筆勢</span><span class="sxs-lookup"><span data-stu-id="08816-244">Gesture</span></span>](gestures.md)
* [<span data-ttu-id="08816-245">動作控制站</span><span class="sxs-lookup"><span data-stu-id="08816-245">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="08816-246">Voice</span><span class="sxs-lookup"><span data-stu-id="08816-246">Voice</span></span>](voice-input.md)
* [<span data-ttu-id="08816-247">提交至 Microsoft Store 應用程式</span><span class="sxs-lookup"><span data-stu-id="08816-247">Submitting an app to the Microsoft Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="08816-248">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="08816-248">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
