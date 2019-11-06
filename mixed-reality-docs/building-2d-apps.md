---
title: 更新適用于混合現實的 2D UWP 應用程式
description: 本文概述如何更新您現有的2D 通用 Windows 平臺應用程式，以在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式，UWP，一般應用程式，HoloLens，沉浸式耳機，應用程式型號，上一頁按鈕，應用程式行，DPI，解析度，調整
ms.openlocfilehash: 46d2a9ca044dee977faecc84d610dc0811a4bfb7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436972"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a><span data-ttu-id="c6dc0-104">更新適用于混合現實的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-104">Updating 2D UWP apps for mixed reality</span></span>

<span data-ttu-id="c6dc0-105">Windows Mixed Reality 可讓使用者在您的實體或數位世界中，看到像是您一樣的全息影像。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-105">Windows Mixed Reality enables a user to see holograms as if they are right around you, in your physical or digital world.</span></span> <span data-ttu-id="c6dc0-106">在其核心中，HoloLens 和您附加了沉浸式耳機配件的桌上型電腦都是 Windows 10 裝置;這表示您可以在存放區中執行幾乎所有的通用 Windows 平臺（UWP）應用程式，做為2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-106">At its core, both HoloLens and the Desktop PCs you attach immersive headset accessories to are Windows 10 devices; this means that you're able to run almost all of the Universal Windows Platform (UWP) apps in the Store as 2D apps.</span></span>

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a><span data-ttu-id="c6dc0-107">建立適用于混合現實的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-107">Creating a 2D UWP app for mixed reality</span></span>

<span data-ttu-id="c6dc0-108">將2D 應用程式帶入混合現實耳機的第一個步驟，是讓您的應用程式在桌面監視器上以標準2D 應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-108">The first step to bringing a 2D app to mixed reality headsets is to get your app running as a standard 2D app on your desktop monitor.</span></span>

### <a name="building-a-new-2d-uwp-app"></a><span data-ttu-id="c6dc0-109">建立新的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-109">Building a new 2D UWP app</span></span>

<span data-ttu-id="c6dc0-110">若要建立混合現實的新2D 應用程式，您只需要建立標準2D 通用 Windows 平臺（UWP）應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-110">To build a new 2D app for mixed reality, you simply build a standard 2D Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="c6dc0-111">該應用程式不需要進行任何其他應用程式變更，就能在混合現實中以平板電腦的形式執行。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-111">No other app changes are required for that app to then run as a slate in mixed reality.</span></span>

<span data-ttu-id="c6dc0-112">若要開始建立 2D UWP 應用程式，請參閱[建立您的第一個應用程式一](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-112">To get started building a 2D UWP app, check out the [Create your first app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) article.</span></span>

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a><span data-ttu-id="c6dc0-113">將現有的2D 存放區應用程式帶入 UWP</span><span class="sxs-lookup"><span data-stu-id="c6dc0-113">Bringing an existing 2D Store app to UWP</span></span>

<span data-ttu-id="c6dc0-114">如果您在存放區中已經有 2D Windows 應用程式，您必須先確定它是以 Windows 10 通用 Windows 平臺（UWP）為目標。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-114">If you already have a 2D Windows app in the Store, you must first ensure it is targeting the Windows 10 Universal Windows Platform (UWP).</span></span> <span data-ttu-id="c6dc0-115">以下是您目前的商店應用程式可能會遇到的所有潛在起點：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-115">Here are all the potential starting points you may have with your Store app today:</span></span>
<br>

|  <span data-ttu-id="c6dc0-116">起始點</span><span class="sxs-lookup"><span data-stu-id="c6dc0-116">Starting Point</span></span>  |  <span data-ttu-id="c6dc0-117">AppX 資訊清單平臺目標</span><span class="sxs-lookup"><span data-stu-id="c6dc0-117">AppX Manifest Platform Target</span></span>  |  <span data-ttu-id="c6dc0-118">如何讓此通用？</span><span class="sxs-lookup"><span data-stu-id="c6dc0-118">How to make this Universal?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="c6dc0-119">Windows Phone （Silverlight）</span><span class="sxs-lookup"><span data-stu-id="c6dc0-119">Windows Phone (Silverlight)</span></span>  |  <span data-ttu-id="c6dc0-120">Silverlight 應用程式資訊清單</span><span class="sxs-lookup"><span data-stu-id="c6dc0-120">Silverlight App Manifest</span></span> |  <span data-ttu-id="c6dc0-121">[遷移至 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="c6dc0-121">[Migrate to WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span></span> | 
|  <span data-ttu-id="c6dc0-122">Windows Phone 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="c6dc0-122">Windows Phone 8.1 Universal</span></span>  |  <span data-ttu-id="c6dc0-123">8.1 AppX 資訊清單，不包含平臺目標</span><span class="sxs-lookup"><span data-stu-id="c6dc0-123">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="c6dc0-124">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="c6dc0-124">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="c6dc0-125">Windows Store 8</span><span class="sxs-lookup"><span data-stu-id="c6dc0-125">Windows Store 8</span></span>  |  <span data-ttu-id="c6dc0-126">8個不包含平臺目標的 AppX 資訊清單</span><span class="sxs-lookup"><span data-stu-id="c6dc0-126">8 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="c6dc0-127">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="c6dc0-127">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="c6dc0-128">Windows Store 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="c6dc0-128">Windows Store 8.1 Universal</span></span>  |  <span data-ttu-id="c6dc0-129">8.1 AppX 資訊清單，不包含平臺目標</span><span class="sxs-lookup"><span data-stu-id="c6dc0-129">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="c6dc0-130">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="c6dc0-130">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 

<span data-ttu-id="c6dc0-131">如果您目前已將 2D Unity 應用程式建立為 Win32 應用程式（「電腦、Mac & Linux 獨立」組建目標），您可以改為將 Unity 切換為 "通用 Windows 平臺" 組建目標，以混合現實的目標。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-131">If you have a 2D Unity app today built as a Win32 app (the "PC, Mac & Linux Standalone" build target), you can target mixed reality by switching Unity to the "Universal Windows Platform" build target instead.</span></span>

<span data-ttu-id="c6dc0-132">我們將討論您可以使用[下面](#publish-and-maintain-your-universal-app)的 Windows 全像攝影裝置系列，將您的應用程式明確地限制在 HoloLens 上的方式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-132">We'll talk about ways that you can restrict your app specifically to HoloLens using the Windows.Holographic device family [below](#publish-and-maintain-your-universal-app).</span></span>

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a><span data-ttu-id="c6dc0-133">在 Windows Mixed Reality 沉浸式耳機中執行2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-133">Run your 2D app in a Windows Mixed Reality immersive headset</span></span>

<span data-ttu-id="c6dc0-134">如果您已將2D 應用程式部署到您正在開發的桌上型電腦，並在您的監視器上嘗試它，您就已經準備好在沉浸式桌面耳機中試用！</span><span class="sxs-lookup"><span data-stu-id="c6dc0-134">If you've deployed your 2D app to the desktop machine where you are developing and tried it out on your monitor, you're already ready to try it out in an immersive desktop headset!</span></span>

<span data-ttu-id="c6dc0-135">只要移至混合現實耳機內的 [開始] 功能表，即可從該處啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-135">Just go to the Start menu within the mixed reality headset and launch the app from there.</span></span> <span data-ttu-id="c6dc0-136">桌面 shell 和全像攝影介面皆共用相同的 UWP 應用程式集，因此當您從 Visual Studio 部署之後，應用程式應該已經存在。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-136">The desktop shell and the holographic shell both share the same set of UWP apps, and so the app should already be present once you've deployed from Visual Studio.</span></span>

## <a name="targeting-both-immersive-headsets-and-hololens"></a><span data-ttu-id="c6dc0-137">以沉浸式耳機和 HoloLens 為目標</span><span class="sxs-lookup"><span data-stu-id="c6dc0-137">Targeting both immersive headsets and HoloLens</span></span>

<span data-ttu-id="c6dc0-138">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c6dc0-138">Congratulations!</span></span> <span data-ttu-id="c6dc0-139">您的應用程式現在正在使用 Windows 10 通用 Windows 平臺（UWP）。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-139">Your app is now using the Windows 10 Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="c6dc0-140">您的應用程式現在能夠在現今的 Windows 裝置上執行，例如桌上型電腦、行動裝置、Xbox、Windows Mixed Reality 沉浸式耳機和 HoloLens，以及未來的 Windows 裝置。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-140">Your app is now capable of running on today's Windows devices like Desktop, Mobile, Xbox, Windows Mixed Reality immersive headsets, and HoloLens, as well as future Windows devices.</span></span> <span data-ttu-id="c6dc0-141">不過，若要實際以這些裝置為目標，您必須確定應用程式的目標為 Windows 通用裝置系列。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-141">However, to actually target all of those devices, you will need to ensure your app is targeting the Windows.Universal device family.</span></span>

### <a name="change-your-device-family-to-windowsuniversal"></a><span data-ttu-id="c6dc0-142">將您的裝置系列變更為 Windows. 通用</span><span class="sxs-lookup"><span data-stu-id="c6dc0-142">Change your device family to Windows.Universal</span></span>

<span data-ttu-id="c6dc0-143">現在，讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以在 HoloLens 上執行：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-143">Now let's jump into your AppX manifest to ensure your Windows 10 UWP app can run on HoloLens:</span></span>
* <span data-ttu-id="c6dc0-144">使用**Visual Studio**開啟應用程式的方案檔，然後流覽至應用程式套件資訊清單</span><span class="sxs-lookup"><span data-stu-id="c6dc0-144">Open your app's solution file with **Visual Studio** and navigate to the app package manifest</span></span>
* <span data-ttu-id="c6dc0-145">以滑鼠右鍵按一下方案中的**package.appxmanifest.xml**檔案，然後移至 [**查看程式碼**]</span><span class="sxs-lookup"><span data-stu-id="c6dc0-145">Right click the **Package.appxmanifest** file in your Solution and go to **View Code**</span></span><br>
  <span data-ttu-id="c6dc0-146">方案總管中的 ![package.appxmanifest.xml](images/openappxmanifest-500px.png)</span><span class="sxs-lookup"><span data-stu-id="c6dc0-146">![package.appxmanifest in Solution Explorer](images/openappxmanifest-500px.png)</span></span><br>
* <span data-ttu-id="c6dc0-147">確定您的目標平臺是 [相依性] 區段中的 [通用]</span><span class="sxs-lookup"><span data-stu-id="c6dc0-147">Ensure your Target Platform is Windows.Universal in the dependencies section</span></span>
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* <span data-ttu-id="c6dc0-148">另!</span><span class="sxs-lookup"><span data-stu-id="c6dc0-148">Save!</span></span>

<span data-ttu-id="c6dc0-149">如果您未在開發環境中使用 Visual Studio，您可以在您選擇的文字編輯器中開啟**package.appxmanifest.xml** ，以確保您的目標是**Windows. 通用** *y*。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-149">If you do not use Visual Studio for your development environment, you can open **AppXManifest.xml** in the text editor of your choice to ensure you're targeting the **Windows.Universal** *TargetDeviceFamily*.</span></span>

### <a name="run-in-the-hololens-emulator"></a><span data-ttu-id="c6dc0-150">在 HoloLens 模擬器中執行</span><span class="sxs-lookup"><span data-stu-id="c6dc0-150">Run in the HoloLens Emulator</span></span>

<span data-ttu-id="c6dc0-151">現在，您的 UWP 應用程式以 "Windows. 通用" 為目標，讓我們建立您的應用程式，並在[HoloLens 模擬器](using-the-hololens-emulator.md)中執行。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-151">Now that your UWP app targets "Windows.Universal", let's build your app and run it in the [HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
* <span data-ttu-id="c6dc0-152">請確定您已[安裝 HoloLens 模擬器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-152">Make sure you have [installed the HoloLens Emulator](install-the-tools.md).</span></span>
* <span data-ttu-id="c6dc0-153">在 Visual Studio 中，選取您應用程式的**x86**組建設定</span><span class="sxs-lookup"><span data-stu-id="c6dc0-153">In Visual Studio, select the **x86** build configuration for your app</span></span>

  ![Visual Studio 中的 x86 組建設定](images/x86setting.png)<br>
* <span data-ttu-id="c6dc0-155">在 [部署目標] 下拉式功能表中選取 [ **HoloLens 模擬器**]</span><span class="sxs-lookup"><span data-stu-id="c6dc0-155">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span>

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* <span data-ttu-id="c6dc0-157">選取 [ **Debug > 開始進行調試**程式] 以部署您的應用程式並開始進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-157">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="c6dc0-158">模擬器會啟動並執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-158">The emulator will start and run your app.</span></span>
* <span data-ttu-id="c6dc0-159">使用鍵盤、滑鼠和/或 Xbox controller，將您的應用程式放在世界中以啟動它。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-159">With a keyboard, mouse, and/or an Xbox controller, place your app in the world to launch it.</span></span>

  ![已載入 UWP 範例的 HoloLens 模擬器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a><span data-ttu-id="c6dc0-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c6dc0-161">Next steps</span></span>

<span data-ttu-id="c6dc0-162">此時，可能會發生下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-162">At this point, one of two things can happen:</span></span>
1. <span data-ttu-id="c6dc0-163">您的應用程式會在放置於模擬器之後，顯示其啟動狀態並開始執行！</span><span class="sxs-lookup"><span data-stu-id="c6dc0-163">Your app will show its splash and start running after it is placed in the Emulator!</span></span> <span data-ttu-id="c6dc0-164">絕佳!</span><span class="sxs-lookup"><span data-stu-id="c6dc0-164">Awesome!</span></span>
2. <span data-ttu-id="c6dc0-165">或者，在您看到2D 全息式的載入動畫之後，載入將會停止，而您只會在其啟動顯示畫面中看到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-165">Or after you see a loading animation for a 2D hologram, loading will stop and you will just see your app at its splash screen.</span></span> <span data-ttu-id="c6dc0-166">這表示發生錯誤，而且會進行更多調查，以瞭解如何讓您的應用程式在混合現實中運作。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-166">This means that something went wrong and it will take more investigation to understand how to bring your app to life in Mixed Reality.</span></span>

<span data-ttu-id="c6dc0-167">若要取得可能導致 UWP 應用程式無法在 HoloLens 上啟動的原因，您必須進行 debug。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-167">To get to the bottom of what may be causing your UWP app not to start on HoloLens, you'll have to debug.</span></span>

### <a name="running-your-uwp-app-in-the-debugger"></a><span data-ttu-id="c6dc0-168">在偵錯工具中執行 UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-168">Running your UWP app in the debugger</span></span>

<span data-ttu-id="c6dc0-169">這些步驟將逐步引導您使用 Visual Studio 偵錯工具來偵測 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-169">These steps will walk you through debugging your UWP app using the Visual Studio debugger.</span></span>
* <span data-ttu-id="c6dc0-170">如果您尚未這麼做，請在 Visual Studio 中開啟您的方案。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-170">If you haven't already done so, open your solution in Visual Studio.</span></span> <span data-ttu-id="c6dc0-171">將目標變更為**HoloLens 模擬器**和組建設定為**x86**。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-171">Change the target to the **HoloLens Emulator** and the build configuration to **x86**.</span></span>
* <span data-ttu-id="c6dc0-172">選取 [ **Debug > 開始進行調試**程式] 以部署您的應用程式並開始進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-172">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="c6dc0-173">使用您的滑鼠、鍵盤或 Xbox 控制器將應用程式放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-173">Place the app in the world with your mouse, keyboard, or Xbox controller.</span></span>
* <span data-ttu-id="c6dc0-174">Visual Studio 現在應該會在應用程式程式碼中的某處中斷。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-174">Visual Studio should now break somewhere in your app code.</span></span>
  - <span data-ttu-id="c6dc0-175">如果您的應用程式不會因為發生未處理的錯誤而立即損毀或中斷偵錯工具，請執行應用程式核心功能的測試階段，以確定所有專案都在執行中且正常運作。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-175">If your app doesn't immediately crash or break into the debugger because of an unhandled error, then go through a test pass of the core features of your app to make sure everything is running and functional.</span></span> <span data-ttu-id="c6dc0-176">您可能會看到如下圖所示的錯誤（正在處理的內部例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-176">You may see errors like pictured below (internal exceptions that are being handled).</span></span> <span data-ttu-id="c6dc0-177">為確保您不會錯過會影響應用程式體驗的內部錯誤，請執行自動化測試和單元測試，以確定所有專案都會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-177">To ensure you don't miss internal errors that impact the experience of your app, run through your automated tests and unit tests to make sure everything behaves as expected.</span></span>

![已載入具有 UWP 範例的 HoloLens 模擬器，顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a><span data-ttu-id="c6dc0-179">更新您的 UI</span><span class="sxs-lookup"><span data-stu-id="c6dc0-179">Update your UI</span></span>

<span data-ttu-id="c6dc0-180">現在，您的 UWP 應用程式是以2D 全息式的耳機和/或 HoloLens 的形式執行，接下來我們要確定它看起來美觀。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-180">Now that your UWP app is running on immersive headsets and/or HoloLens as a 2D hologram, next we'll make sure it looks beautiful.</span></span> <span data-ttu-id="c6dc0-181">以下是一些要考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-181">Here are some things to consider:</span></span>
* <span data-ttu-id="c6dc0-182">Windows Mixed Reality 會以固定解析度和 DPI （等同于853x480 有效圖元）來執行所有2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-182">Windows Mixed Reality will run all 2D apps at a fixed resolution and DPI that equates to 853x480 effective pixels.</span></span> <span data-ttu-id="c6dc0-183">請考慮您的設計是否需要調整規模，並回顧下面的設計指引，以改善 HoloLens 和沉浸式耳機的體驗。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-183">Consider if your design needs refinement at this scale and review the design guidance below to improve your experience on HoloLens and immersive headsets.</span></span>
* <span data-ttu-id="c6dc0-184">Windows Mixed Reality 不[支援](app-model.md)2d 動態磚。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-184">Windows Mixed Reality [does not support](app-model.md) 2D live tiles.</span></span> <span data-ttu-id="c6dc0-185">如果您的核心功能顯示動態磚上的資訊，請考慮將該資訊移回您的應用程式，或探索[3d 應用程式啟動器](3d-app-launcher-design-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-185">If your core functionality is showing information on a live tile, consider moving that information back into your app or explore [3D app launchers](3d-app-launcher-design-guidance.md).</span></span>

### <a name="2d-app-view-resolution-and-scale-factor"></a><span data-ttu-id="c6dc0-186">2D 應用程式視圖解析度和縮放比例</span><span class="sxs-lookup"><span data-stu-id="c6dc0-186">2D app view resolution and scale factor</span></span>

![從回應式設計](images/scale-500px.png)

<span data-ttu-id="c6dc0-188">Windows 10 會將所有視覺化設計從真實的螢幕圖元移到**有效的圖元**。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-188">Windows 10 moves all visual design from real screen pixels to **effective pixels**.</span></span> <span data-ttu-id="c6dc0-189">這表示，開發人員會遵循 Windows 10 人力介面指導方針來設計其 UI 以取得有效的圖元，而 Windows 調整可確保這些有效圖元的大小適合跨裝置、解析度、DPI 等的可用性。如需深入瞭解和此[組建簡報](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)，請參閱[MSDN 上的這篇絕佳的閱讀](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-189">That means, developers design their UI following the Windows 10 Human Interface Guidelines for effective pixels, and Windows scaling ensures those effective pixels are the right size for usability across devices, resolutions, DPI, etc. See this [great read on MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) to learn more as well as this [BUILD presentation](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).</span></span>

<span data-ttu-id="c6dc0-190">即使是將應用程式放在世界各地的獨特功能，也建議使用類似電視的視圖距離，以產生最佳的可讀性，並與注視/手勢互動。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-190">Even with the unique ability to place apps in your world at a range of distances, TV-like viewing distances are recommended to produce the best readability and interaction with gaze/gesture.</span></span> <span data-ttu-id="c6dc0-191">因此，混合現實家中的虛擬平板電腦會顯示您的一般 UWP 視圖，網址為：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-191">Because of that, a virtual slate in the Mixed Reality Home will display your flat UWP view at:</span></span>

<span data-ttu-id="c6dc0-192">**1280x720，150% DPI** （853x480 有效圖元）</span><span class="sxs-lookup"><span data-stu-id="c6dc0-192">**1280x720, 150%DPI** (853x480 effective pixels)</span></span>

<span data-ttu-id="c6dc0-193">此解決方案有幾個優點：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-193">This resolution has several advantages:</span></span>
* <span data-ttu-id="c6dc0-194">這種有效的圖元版面配置與平板電腦或小型桌面的資訊密度相同。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-194">This effective pixel layout will have about the same information density as a tablet or small desktop.</span></span>
* <span data-ttu-id="c6dc0-195">它會比對在 Xbox One 上執行之 UWP 應用程式的固定 DPI 和有效圖元，讓裝置之間的順暢體驗。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-195">It matches the fixed DPI and effective pixels for UWP apps running on Xbox One, enabling seamless experiences across devices.</span></span>
* <span data-ttu-id="c6dc0-196">在世界各地應用程式的營運距離範圍內調整時，此大小看起來很好。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-196">This size looks good when scaled across our range of operating distances for apps in the world.</span></span>

### <a name="2d-app-view-interface-design-best-practices"></a><span data-ttu-id="c6dc0-197">2D 應用程式視圖介面設計最佳做法</span><span class="sxs-lookup"><span data-stu-id="c6dc0-197">2D app view interface design best practices</span></span>

<span data-ttu-id="c6dc0-198">**對**</span><span class="sxs-lookup"><span data-stu-id="c6dc0-198">**Do:**</span></span>
* <span data-ttu-id="c6dc0-199">遵循[Windows 10 人力介面指導方針（HIG）](https://dev.windows.com/design)以取得樣式、字型大小和按鈕大小。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-199">Follow the [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) for styles, font sizes and button sizes.</span></span> <span data-ttu-id="c6dc0-200">HoloLens 會執行工作，以確保您的應用程式會有相容的應用程式模式、可讀取的文字大小，以及適當的點擊目標大小。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-200">HoloLens will do the work to ensure your app will have compatible app patterns, readable text sizes, and appropriate hit target sizing.</span></span>
* <span data-ttu-id="c6dc0-201">請確定您的 UI 遵循最佳做法，讓[回應式設計](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)在 HoloLen 的獨特解析度和 DPI 上的外觀最佳。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-201">Ensure your UI follows best practices for [responsive design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) to look best at HoloLen's unique resolution and DPI.</span></span>
* <span data-ttu-id="c6dc0-202">使用 Windows 的「淺色」色彩主題建議。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-202">Use the "light" color theme recommendations from Windows.</span></span>

<span data-ttu-id="c6dc0-203">**不要：**</span><span class="sxs-lookup"><span data-stu-id="c6dc0-203">**Don't:**</span></span>
* <span data-ttu-id="c6dc0-204">在混合的現實中，變更您的 UI 太大，以確保使用者在耳機中有熟悉的體驗。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-204">Change your UI too drastically when in mixed reality, to ensure users have a familiar experience in and out of the headset.</span></span>

### <a name="understand-the-app-model"></a><span data-ttu-id="c6dc0-205">瞭解應用程式模型</span><span class="sxs-lookup"><span data-stu-id="c6dc0-205">Understand the app model</span></span>

<span data-ttu-id="c6dc0-206">混合式現實的[應用程式模型](app-model.md)是設計用來使用混合現實首頁，其中許多應用程式都在一起運作。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-206">The [app model](app-model.md) for mixed reality is designed to use the Mixed Reality Home, where many apps live together.</span></span> <span data-ttu-id="c6dc0-207">請將此視為桌上型電腦的混合現實，您可以在其中一次執行許多2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-207">Think of this as the mixed reality equivalent of the desktop, where you run many 2D apps at once.</span></span> <span data-ttu-id="c6dc0-208">這對應用程式的生命週期、磚和其他主要功能有一些影響。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-208">This has implications on app life cycle, Tiles, and other key features of your app.</span></span>

### <a name="app-bar-and-back-button"></a><span data-ttu-id="c6dc0-209">[應用程式行] 和 [上一頁] 按鈕</span><span class="sxs-lookup"><span data-stu-id="c6dc0-209">App bar and back button</span></span>

<span data-ttu-id="c6dc0-210">2D 視圖會使用其內容上方的應用程式行裝飾。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-210">2D views are decorated with a app bar above their content.</span></span> <span data-ttu-id="c6dc0-211">應用程式行有兩個應用程式專屬個人化的點：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-211">The app bar has two points of app-specific personalization:</span></span>

<span data-ttu-id="c6dc0-212">**標題：** 顯示與應用程式實例相關聯之磚的*displayname*</span><span class="sxs-lookup"><span data-stu-id="c6dc0-212">**Title:** displays the *displayname* of the Tile associated with the app instance</span></span>

<span data-ttu-id="c6dc0-213">**上一頁按鈕：** 當按下時，會引發 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 事件。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-213">**Back Button:** raises the *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* event when pressed.</span></span> <span data-ttu-id="c6dc0-214">[上一頁] 按鈕可見度是由 *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 所控制。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-214">Back Button visibility is controlled by *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.</span></span>

<span data-ttu-id="c6dc0-215">![2D 應用程式視圖中的應用程式行 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6dc0-215">![App bar UI in 2D app view](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span></span><br>
<span data-ttu-id="c6dc0-216">*2D 應用程式視圖中的應用程式行 UI*</span><span class="sxs-lookup"><span data-stu-id="c6dc0-216">*App bar UI in 2D app view*</span></span>

### <a name="test-your-2d-apps-design"></a><span data-ttu-id="c6dc0-217">測試您的2D 應用程式設計</span><span class="sxs-lookup"><span data-stu-id="c6dc0-217">Test your 2D app's design</span></span>

<span data-ttu-id="c6dc0-218">請務必測試您的應用程式，以確定文字可供讀取、按鈕為目標設為，且整體應用程式看起來是正確的。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-218">It is important to test your app to make sure the text is readable, the buttons are targetable, and the overall app looks correct.</span></span> <span data-ttu-id="c6dc0-219">您可以在桌面耳機、HoloLens、模擬器或將解析度設定為 1280x720 % 的觸控裝置上進行[測試](testing-your-app-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-219">You can [test](testing-your-app-on-hololens.md) on a desktop headset, a HoloLens, an emulator, or a touch device with resolution set to 1280x720 @150%.</span></span>

## <a name="new-input-possibilities"></a><span data-ttu-id="c6dc0-220">新的輸入可能性</span><span class="sxs-lookup"><span data-stu-id="c6dc0-220">New input possibilities</span></span>

<span data-ttu-id="c6dc0-221">HoloLens 使用先進的深度感應器來查看世界並查看使用者。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-221">HoloLens uses advanced depth sensors to see the world and see users.</span></span> <span data-ttu-id="c6dc0-222">這可啟用先進的手勢，例如[bloom](system-gesture.md#bloom)和[空中碰](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-222">This enables advanced hand gestures like [bloom](system-gesture.md#bloom) and [air-tap](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="c6dc0-223">強大的麥克風也可以提供[語音體驗](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-223">Powerful microphones also enable [voice experiences](voice-input.md).</span></span>

<span data-ttu-id="c6dc0-224">使用桌面耳機時，使用者可以使用動作控制器來指向應用程式並採取動作。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-224">With Desktop headsets, users can use motion controllers to point at apps and take action.</span></span> <span data-ttu-id="c6dc0-225">他們也可以使用遊戲台，以物件與其注視的目標。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-225">They can also use a gamepad, targeting objects with their gaze.</span></span>

<span data-ttu-id="c6dc0-226">Windows 會負責 UWP 應用程式的所有這項複雜性，將您的[注視](gaze-and-commit.md)、手勢、語音和動作控制器輸入，轉譯為會抽象化輸入機制的[指標事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-226">Windows takes care of all of this complexity for UWP apps, translating your [gaze](gaze-and-commit.md), gestures, voice and motion controller input to [pointer events](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) that abstract away the input mechanism.</span></span> <span data-ttu-id="c6dc0-227">例如，使用者可能已在動作控制器上使用手或拉出選取觸發程式，但2D 應用程式不需要知道輸入來自何處-它們只會看到2D 觸控按，如同在觸控式螢幕上一樣。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-227">For example, a user may have done an air-tap with their hand or pulled the Select trigger on a motion controller, but 2D applications don't need to know where the input came from - they just see a 2D touch press, as if on a touchscreen.</span></span>

<span data-ttu-id="c6dc0-228">以下是將 UWP 應用程式帶入 HoloLens 時，您應該瞭解的高階概念/案例：</span><span class="sxs-lookup"><span data-stu-id="c6dc0-228">Here are the high level concepts/scenarios you should understand for input when bringing your UWP app to HoloLens:</span></span>
* <span data-ttu-id="c6dc0-229">[看一下](gaze-and-commit.md)暫留事件, 這可能會非預期地觸發功能表、flyouts 或其他使用者介面元素, 只要撥雲見日應用程式就能快顯。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-229">[Gaze](gaze-and-commit.md) turns into hover events, which can unexpectedly trigger menus, flyouts or other user interface elements to pop up just by gazing around your app.</span></span>
* <span data-ttu-id="c6dc0-230">注視並不像滑鼠輸入一樣精確。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-230">Gaze is not as precise as mouse input.</span></span> <span data-ttu-id="c6dc0-231">針對 HoloLens 使用適當大小的叫用目標，類似于觸控式行動裝置應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-231">Use appropriately sized hit targets for HoloLens, similar to touch-friendly mobile applications.</span></span> <span data-ttu-id="c6dc0-232">接近應用程式邊緣的小型元素尤其難以與互動。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-232">Small elements near the edges of the app are especially hard to interact with.</span></span>
* <span data-ttu-id="c6dc0-233">使用者必須將輸入模式切換成從滾動拖曳至兩個手指移動。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-233">Users must switch input modes to go from scrolling to dragging to two finger panning.</span></span> <span data-ttu-id="c6dc0-234">如果您的應用程式是針對觸控輸入而設計，請考慮確保不會在兩個手指移動後鎖定任何主要功能。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-234">If your app was designed for touch input, consider ensuring that no major functionality is locked behind two finger panning.</span></span> <span data-ttu-id="c6dc0-235">若是如此，請考慮具有替代的輸入機制，例如可以起始兩個手指移動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-235">If so, consider having alternative input mechanisms like buttons that can initiate two finger panning.</span></span> <span data-ttu-id="c6dc0-236">例如，地圖應用程式可以使用兩個手指移動來縮放，但有一個加號、減號和旋轉按鈕，可透過按一下來模擬相同的縮放互動。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-236">For example, the Maps app can zoom with two finger panning but has a plus, minus, and rotate button to simulate the same zoom interactions with single clicks.</span></span>

<span data-ttu-id="c6dc0-237">[語音輸入](voice-input.md)是混合現實體驗的重要部分。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-237">[Voice input](voice-input.md) is a critical part of the mixed reality experience.</span></span> <span data-ttu-id="c6dc0-238">我們已在使用耳機時，啟用 Windows 10 中的所有語音 Api。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-238">We've enabled all of the speech APIs that are in Windows 10 powering Cortana when using a headset.</span></span>

## <a name="publish-and-maintain-your-universal-app"></a><span data-ttu-id="c6dc0-239">發行和維護您的通用應用程式</span><span class="sxs-lookup"><span data-stu-id="c6dc0-239">Publish and Maintain your Universal app</span></span>

<span data-ttu-id="c6dc0-240">當您的應用程式啟動並執行之後，請封裝您的應用程式，將[它提交至 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dc0-240">Once your app is up and running, package your app to [submit it to the Microsoft Store](submitting-an-app-to-the-microsoft-store.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6dc0-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6dc0-241">See also</span></span>
* [<span data-ttu-id="c6dc0-242">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="c6dc0-242">App model</span></span>](app-model.md)
* [<span data-ttu-id="c6dc0-243">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="c6dc0-243">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c6dc0-244">運動控制器</span><span class="sxs-lookup"><span data-stu-id="c6dc0-244">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="c6dc0-245">語音輸入</span><span class="sxs-lookup"><span data-stu-id="c6dc0-245">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="c6dc0-246">將應用程式提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c6dc0-246">Submitting an app to the Microsoft Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="c6dc0-247">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="c6dc0-247">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
