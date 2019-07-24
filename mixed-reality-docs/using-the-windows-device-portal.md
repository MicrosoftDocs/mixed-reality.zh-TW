---
title: 使用 Windows 裝置入口網站
description: 適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具, 可協助您管理 HoloLens 並對應用程式進行優化和優化。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 裝置入口網站、HoloLens
ms.openlocfilehash: 79a4a1f99125028fcaf71e185eb00093aa8c742f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694587"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="6ff7e-106">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="6ff7e-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="6ff7e-107">功能</span><span class="sxs-lookup"><span data-stu-id="6ff7e-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="6ff7e-108"><a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="6ff7e-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="6ff7e-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6ff7e-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="6ff7e-110"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="6ff7e-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="6ff7e-111">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="6ff7e-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ff7e-112">✔️</span><span class="sxs-lookup"><span data-stu-id="6ff7e-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ff7e-113">✔️</span><span class="sxs-lookup"><span data-stu-id="6ff7e-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="6ff7e-114">適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="6ff7e-115">Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="6ff7e-116">裝置入口網站包含許多工具, 可協助您管理 HoloLens 並對應用程式進行優化和優化。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="6ff7e-117">本檔特別說明適用于 HoloLens 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="6ff7e-118">若要使用適用于桌面的 Windows 裝置入口網站 (包括 Windows Mixed Reality), 請參閱[Windows 裝置入口網站總覽](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="6ff7e-119">設定 HoloLens 以使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="6ff7e-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="6ff7e-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="6ff7e-121">做出[盛開](gestures.md#bloom)手勢來啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-121">Perform the [bloom](gestures.md#bloom) gesture to launch the main menu.</span></span>
3. <span data-ttu-id="6ff7e-122">注視 [**設定**] 圖格, 然後執行 [[空中](gestures.md#air-tap)] 手勢。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-122">Gaze at the **Settings** tile and perform the [air-tap](gestures.md#air-tap) gesture.</span></span> <span data-ttu-id="6ff7e-123">執行第二個按鍵, 將應用程式放在您的環境中。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-123">Perform a second air-tap to place the app in your environment.</span></span> <span data-ttu-id="6ff7e-124">當您放置 [設定] App 之後，該 App 便會啟動。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-124">The Settings app will launch after you place it.</span></span>
4. <span data-ttu-id="6ff7e-125">選取 [更新] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-125">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="6ff7e-126">選取 [適用於開發人員] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-126">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="6ff7e-127">啟用 [開發人員模式]。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-127">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="6ff7e-128">[向下滾動](gestures.md#composite-gestures)並啟用 [**裝置入口網站**]。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-128">[Scroll down](gestures.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="6ff7e-129">如果您要設定 Windows 裝置入口網站, 讓您可以透過 USB 或 Wi-fi 將應用程式部署到此 HoloLens, 請按一下 [**配對**] 以[產生配對 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-129">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="6ff7e-130">將 [設定] 應用程式保留在 [PIN] 快顯視窗中, 直到您在第一次部署期間輸入 Visual Studio 的 PIN 為止。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-130">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="6ff7e-132">透過 Wi-fi 連接</span><span class="sxs-lookup"><span data-stu-id="6ff7e-132">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="6ff7e-133">[將 HoloLens 連接至 wi-fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-133">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="6ff7e-134">查詢您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-134">Look up your device's IP address.</span></span>
   * <span data-ttu-id="6ff7e-135">在 [設定] 底下的裝置上尋找 IP 位址 **> 網路 & 網際網路 > wi-fi > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-135">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="6ff7e-136">從您電腦上的網頁瀏覽器, 移至 HTTPs://< YOUR_HOLOLENS_IP_ADDRESS ></span><span class="sxs-lookup"><span data-stu-id="6ff7e-136">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="6ff7e-137">瀏覽器將會顯示下列訊息:「此網站的安全性憑證有問題」。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-137">The browser will display the following message: "There’s a problem with this website’s security certificate".</span></span> <span data-ttu-id="6ff7e-138">這是因為核發給 Device Portal 的憑證是測試憑證。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-138">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="6ff7e-139">您可以暫時略過這個憑證錯誤並繼續。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-139">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="6ff7e-140">透過 USB 連接</span><span class="sxs-lookup"><span data-stu-id="6ff7e-140">Connecting over USB</span></span>

1. <span data-ttu-id="6ff7e-141">[安裝工具](install-the-tools.md), 以確定您已在電腦上安裝 Windows 10 開發人員工具來執行 Visual Studio Update 1。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-141">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="6ff7e-142">這將能啟用 USB 連線能力。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-142">This enables USB connectivity.</span></span>
2. <span data-ttu-id="6ff7e-143">透過 Micro-USB 纜線將您的 HoloLens 與電腦連接。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-143">Connect your HoloLens to your PC with a micro-USB cable.</span></span>
3. <span data-ttu-id="6ff7e-144">從您電腦上的網頁瀏覽器，移至 http://127.0.0.1:10080 。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-144">From a web browser on your PC, go to http://127.0.0.1:10080.</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="6ff7e-145">連接到模擬器</span><span class="sxs-lookup"><span data-stu-id="6ff7e-145">Connecting to an emulator</span></span>

<span data-ttu-id="6ff7e-146">您也可以透過模擬器使用 Device Portal。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-146">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="6ff7e-147">若要連接到裝置入口網站, 請使用[工具列](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-147">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="6ff7e-148">按一下這個圖示：![開啟裝置入口網站](images/emulator-deviceportal.png)圖示**開啟裝置入口網站**:在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-148">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="6ff7e-149">建立使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="6ff7e-149">Creating a Username and Password</span></span>

<span data-ttu-id="6ff7e-150">![設定 Windows 裝置入口網站的存取權](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-150">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-151">*設定 Windows 裝置入口網站的存取權*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-151">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="6ff7e-152">首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-152">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="6ff7e-153">在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-153">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="6ff7e-154">[設定存取] 頁面將會開啟。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-154">The Set up access page opens.</span></span>
2. <span data-ttu-id="6ff7e-155">按一下或點擊 [**要求 pin** ], 並查看 HoloLens 顯示以取得產生的 pin。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-155">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="6ff7e-156">在 [**您的裝置上顯示的 pin** ] 文字方塊中輸入 pin。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-156">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="6ff7e-157">輸入您會用來連線到 Device Portal 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-157">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="6ff7e-158">它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-158">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="6ff7e-159">輸入密碼並確認它。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-159">Enter a password and confirm it.</span></span> <span data-ttu-id="6ff7e-160">密碼長度必須至少為七個字元。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-160">The password must be at least seven characters in length.</span></span> <span data-ttu-id="6ff7e-161">它並不需要是 MSA 或網域密碼。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-161">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="6ff7e-162">按一下 [**配對**] 以連線至 HoloLens 上的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-162">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="6ff7e-163">如果您想要隨時變更此使用者名稱或密碼, 您可以流覽至: HTTPs://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm., 藉此重複此程式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-163">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="6ff7e-164">安全性憑證</span><span class="sxs-lookup"><span data-stu-id="6ff7e-164">Security certificate</span></span>

<span data-ttu-id="6ff7e-165">如果您在瀏覽器中看見「憑證錯誤」，您可以透過和裝置建立信任關係來修正它。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-165">If you are see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="6ff7e-166">每個 HoloLens 都會為其 SSL 連線產生唯一的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-166">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="6ff7e-167">根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-167">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="6ff7e-168">藉由從您的 HoloLens 下載此憑證 (透過 USB 或您信任的 Wi-Fi 網路)，並在電腦上信任它，您便能安全地連線到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-168">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="6ff7e-169">**請確定您使用的是安全的網路 (USB 或您信任的 Wi-fi 網路)。**</span><span class="sxs-lookup"><span data-stu-id="6ff7e-169">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="6ff7e-170">從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-170">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="6ff7e-171">流覽至: HTTPs://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="6ff7e-171">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
3. <span data-ttu-id="6ff7e-172">將憑證安裝在您電腦上的「受信任的根憑證授權」存放區中。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="6ff7e-173">從 [Windows] 功能表中, 輸入:管理電腦憑證並啟動 applet。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="6ff7e-174">展開 [**信任的根憑證授權**單位] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="6ff7e-175">按一下 [**憑證**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-175">Click on the **Certificates** folder.</span></span>
   * <span data-ttu-id="6ff7e-176">從 [動作] 功能表中, 選取:所有工作 > 匯入 。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="6ff7e-177">使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="6ff7e-178">重新啟動瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-178">Restart the browser.</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="6ff7e-179">Device Portal 頁面</span><span class="sxs-lookup"><span data-stu-id="6ff7e-179">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="6ff7e-180">首頁</span><span class="sxs-lookup"><span data-stu-id="6ff7e-180">Home</span></span>

<span data-ttu-id="6ff7e-181">![Microsoft HoloLens 上的 Windows 裝置入口網站首頁](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-181">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-182">*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-182">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-183">您的 Device Portal 工作階段從首頁開始。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-183">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="6ff7e-184">從首頁左側的瀏覽列中存取其他頁面。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-184">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="6ff7e-185">頁面頂端的工具列能讓您存取常用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-185">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="6ff7e-186">**線上**:指出裝置是否已連線至 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-186">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="6ff7e-187">**關機**:關閉裝置。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-187">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="6ff7e-188">**重新開機**:迴圈裝置上的電源。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-188">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="6ff7e-189">**安全性**:開啟 [裝置安全性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-189">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="6ff7e-190">**酷炫**:表示裝置的溫度。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-190">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="6ff7e-191">**A/C**:指出裝置是否已插入並收費。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-191">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="6ff7e-192">說明:開啟 REST 介面檔頁面。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-192">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="6ff7e-193">首頁將顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6ff7e-193">The home page shows the following info:</span></span>
* <span data-ttu-id="6ff7e-194">**裝置狀態:** 監視裝置的健全狀況, 並回報重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-194">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="6ff7e-195">**Windows 資訊:** 顯示 HoloLens 的名稱和目前安裝的 windows 版本。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-195">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="6ff7e-196">[喜好設定] 區段包含下列設定：</span><span class="sxs-lookup"><span data-stu-id="6ff7e-196">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="6ff7e-197">**IPD**:設定 interpupillary 距離 (IPD), 這是使用者的瞳孔在直接查看時的中心之間的距離 (以毫米為單位)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-197">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="6ff7e-198">此設定會立即生效。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-198">The setting takes effect immediately.</span></span> <span data-ttu-id="6ff7e-199">預設值會在您設定裝置時自動計算。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-199">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="6ff7e-200">**裝置名稱**:將名稱指派給 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-200">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="6ff7e-201">在變更此值之後，必須重新啟動裝置才能生效。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-201">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="6ff7e-202">按一下 [**儲存**] 之後, 對話方塊會詢問您是否要立即重新開機裝置, 或稍後重新開機。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-202">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="6ff7e-203">**睡眠設定**:設定當裝置插入電源且電池在使用中時, 要等待的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-203">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="6ff7e-204">3D 檢視</span><span class="sxs-lookup"><span data-stu-id="6ff7e-204">3D View</span></span>

<span data-ttu-id="6ff7e-205">![Microsoft HoloLens 上 Windows 裝置入口網站中的 3D View 頁面](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-205">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-206">*Microsoft HoloLens 上 Windows 裝置入口網站中的 3D View 頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-206">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-207">使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-207">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="6ff7e-208">使用滑鼠來瀏覽檢視：</span><span class="sxs-lookup"><span data-stu-id="6ff7e-208">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="6ff7e-209">旋轉: 按滑鼠左鍵 + 滑鼠;</span><span class="sxs-lookup"><span data-stu-id="6ff7e-209">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="6ff7e-210">Pan: 以滑鼠右鍵按一下滑鼠;</span><span class="sxs-lookup"><span data-stu-id="6ff7e-210">Pan: right click + mouse;</span></span>
* <span data-ttu-id="6ff7e-211">Zoom: 滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-211">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="6ff7e-212">**追蹤選項**</span><span class="sxs-lookup"><span data-stu-id="6ff7e-212">**Tracking options**</span></span>
   * <span data-ttu-id="6ff7e-213">藉由勾選 [**強制視覺效果追蹤**], 開啟連續視覺效果追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-213">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="6ff7e-214">[**暫停**] 會停止視覺效果追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-214">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="6ff7e-215">**視圖選項**:在3D 視圖上設定選項:</span><span class="sxs-lookup"><span data-stu-id="6ff7e-215">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="6ff7e-216">**追蹤**:指出視覺效果追蹤是否作用中。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-216">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="6ff7e-217">**顯示樓層**:顯示棋盤地板平面。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-217">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="6ff7e-218">**顯示截錐**:顯示視圖的「截錐」。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-218">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="6ff7e-219">**顯示穩定平面**:顯示 HoloLens 用來進行穩定動作的平面。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-219">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="6ff7e-220">**顯示網格**:顯示代表您周圍的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-220">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="6ff7e-221">**顯示空間錨點**:顯示作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-221">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="6ff7e-222">您必須按一下 [更新] 按鈕, 才能取得並重新整理錨點。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-222">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="6ff7e-223">**顯示詳細資料**:顯示手的位置、前端旋轉四元數, 以及裝置原點向量 (當它們即時變更時)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-223">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="6ff7e-224">**全螢幕按鈕**:以全螢幕模式顯示3D 視圖。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-224">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="6ff7e-225">按下 ESC 以離開全螢幕檢視。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-225">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="6ff7e-226">**表面重建**:按一下或按 [**更新**], 以顯示裝置中最新的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-226">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="6ff7e-227">可能需要花費一些時間 (最多幾秒鐘) 才能完成完整作業。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-227">A full pass may take some time to complete, up to a few seconds.</span></span> <span data-ttu-id="6ff7e-228">網格不會在3D 視圖中自動更新, 您必須手動按一下 [**更新**], 從裝置取得最新的網格。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-228">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="6ff7e-229">按一下 [**儲存**], 將目前的空間對應網格儲存為電腦上的 obj 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-229">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="6ff7e-230">**空間錨點**:按一下 [更新] 以顯示或更新作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-230">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="6ff7e-231">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="6ff7e-231">Mixed Reality Capture</span></span>

<span data-ttu-id="6ff7e-232">![Microsoft HoloLens 上 Windows 裝置入口網站中的混合現實 Capture 頁面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-232">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-233">*Microsoft HoloLens 上 Windows 裝置入口網站中的混合現實 Capture 頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-233">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-234">使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-234">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="6ff7e-235">**設定**:藉由檢查下列設定來控制所捕捉的媒體串流:</span><span class="sxs-lookup"><span data-stu-id="6ff7e-235">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="6ff7e-236">**全息影像**:在影片串流中捕捉全像攝影內容。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-236">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="6ff7e-237">全像投影是以單聲道進行轉譯，而非立體聲。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-237">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="6ff7e-238">**PV 攝影機**:從相片/攝影機捕捉影片串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-238">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="6ff7e-239">**Mic 音訊**:從麥克風陣列捕捉音訊。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-239">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="6ff7e-240">**應用程式音訊**:從目前執行中的應用程式捕捉音訊。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-240">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="6ff7e-241">**從相機**轉譯:如果執行中的[應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), 則將捕捉從相片/攝影機的角度對齊 (僅限 HoloLens 2)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-241">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="6ff7e-242">**Live preview 品質**:選取 [螢幕解析度]、[畫面播放速率] 和 [即時預覽的串流速率]。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-242">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="6ff7e-243">按一下或點擊 [**即時預覽**] 按鈕以顯示 capture 串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-243">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="6ff7e-244">[**停止即時預覽**] 會停止 capture 串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-244">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="6ff7e-245">按一下或按下 [**記錄**], 以使用指定的設定開始記錄混合現實串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-245">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="6ff7e-246">[**停止錄製**] 會結束錄製並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-246">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="6ff7e-247">按一下或點擊 [**拍攝相片**], 從 capture 串流拍攝靜止的影像。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-247">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="6ff7e-248">影片**和相片**:顯示在裝置上拍攝的影片和相片捕捉清單。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-248">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="6ff7e-249">[同時 MRC 的限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)如下:</span><span class="sxs-lookup"><span data-stu-id="6ff7e-249">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="6ff7e-250">如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機, 影片錄製將會停止。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-250">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="6ff7e-251">如果應用程式使用 SharedReadOnly 模式 acesses 相片/攝影機, 則 HoloLens 2 不會停止錄製影片。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-251">HoloLens 2 will not stop recording video if the app acesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="6ff7e-252">如果應用程式正在使用相片/攝影機, Windows 裝置入口網站就能夠拍攝相片或錄製影片。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-252">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="6ff7e-253">即時串流:</span><span class="sxs-lookup"><span data-stu-id="6ff7e-253">Live streaming:</span></span>
>   * <span data-ttu-id="6ff7e-254">HoloLens (第1代) 可防止應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-254">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="6ff7e-255">如果應用程式正在使用相片/攝影機, HoloLens (第1代) 將無法即時串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-255">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="6ff7e-256">當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時, HoloLens 2 會自動停止即時串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-256">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="6ff7e-257">當應用程式主動使用 PV 攝影機時, HoloLens 2 可以啟動即時串流。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-257">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="6ff7e-258">效能追蹤</span><span class="sxs-lookup"><span data-stu-id="6ff7e-258">Performance Tracing</span></span>

<span data-ttu-id="6ff7e-259">![Microsoft HoloLens 上 Windows 裝置入口網站中的效能追蹤頁面](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-259">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-260">*Microsoft HoloLens 上 Windows 裝置入口網站中的效能追蹤頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-260">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-261">從 HoloLens 捕獲[Windows 效能錄製](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)器 (WPR) 追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-261">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="6ff7e-262">**可用的設定檔**:從下拉式清單中選取 WPR 設定檔, 然後按一下或按 [**啟動**] 開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-262">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="6ff7e-263">**自訂設定檔**:按一下或點擊 **[流覽]** , 從您的電腦選擇 WPR 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-263">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="6ff7e-264">按一下或點選 [上傳並開始] 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-264">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="6ff7e-265">若要停止追蹤, 請按一下 [停止] 連結。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-265">To stop the trace click on the stop link.</span></span> <span data-ttu-id="6ff7e-266">在追蹤檔案下載完成之前, 請停留在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-266">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="6ff7e-267">擷取的 ETL 檔案可以在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中開啟以進行分析。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-267">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="6ff7e-268">處理程序</span><span class="sxs-lookup"><span data-stu-id="6ff7e-268">Processes</span></span>

<span data-ttu-id="6ff7e-269">![Microsoft HoloLens 上 Windows 裝置入口網站中的 [進程] 頁面](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-269">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-270">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [進程] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-270">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-271">顯示有關目前正在執行之處理程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-271">Shows details about currently running processes.</span></span> <span data-ttu-id="6ff7e-272">這包括 App 與系統處理程序。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-272">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="6ff7e-273">系統效能</span><span class="sxs-lookup"><span data-stu-id="6ff7e-273">System Performance</span></span>

<span data-ttu-id="6ff7e-274">![Microsoft HoloLens 上 Windows 裝置入口網站中的 [系統效能] 頁面](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-274">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-275">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [系統效能] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-275">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-276">顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-276">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="6ff7e-277">下列為可用的衡量標準：</span><span class="sxs-lookup"><span data-stu-id="6ff7e-277">These are the available metrics:</span></span>
* <span data-ttu-id="6ff7e-278">**SoC 電源**:瞬間的系統晶片電源使用率, 平均超過一分鐘</span><span class="sxs-lookup"><span data-stu-id="6ff7e-278">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="6ff7e-279">**系統電源**:瞬間系統電源使用率, 平均超過一分鐘</span><span class="sxs-lookup"><span data-stu-id="6ff7e-279">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="6ff7e-280">**畫面播放速率**:每秒畫面數、每秒錯過的 VBlanks, 以及連續錯過的 VBlanks</span><span class="sxs-lookup"><span data-stu-id="6ff7e-280">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="6ff7e-281">**GPU**:GPU 引擎使用率, 總可用百分比</span><span class="sxs-lookup"><span data-stu-id="6ff7e-281">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="6ff7e-282">**CPU**: 可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="6ff7e-282">**CPU**: percent of total available</span></span>
* <span data-ttu-id="6ff7e-283">**I/O**:讀取和寫入</span><span class="sxs-lookup"><span data-stu-id="6ff7e-283">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="6ff7e-284">**網路**：已接收和已傳送</span><span class="sxs-lookup"><span data-stu-id="6ff7e-284">**Network**: Received and sent</span></span>
* <span data-ttu-id="6ff7e-285">**記憶體**:總計、使用中、已認可、已分頁和未分頁</span><span class="sxs-lookup"><span data-stu-id="6ff7e-285">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="6ff7e-286">應用程式</span><span class="sxs-lookup"><span data-stu-id="6ff7e-286">Apps</span></span>

<span data-ttu-id="6ff7e-287">![Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式頁面](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-287">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-288">*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-288">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-289">管理安裝在 HoloLens 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-289">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="6ff7e-290">**已安裝的應用程式**:移除並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-290">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="6ff7e-291">**正在執行應用程式**:列出目前正在執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-291">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="6ff7e-292">**安裝應用程式**:從您電腦/網路上的資料夾選取要安裝的應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-292">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="6ff7e-293">相依性:新增您即將安裝之應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-293">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="6ff7e-294">**部署**:將選取的應用程式 + 相依性部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-294">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="6ff7e-295">應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="6ff7e-295">App Crash Dumps</span></span>

<span data-ttu-id="6ff7e-296">![Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式損毀傾印頁面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-296">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-297">*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式損毀傾印頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-297">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-298">此頁面可讓您收集側載 App 的損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-298">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="6ff7e-299">針對您要收集損毀傾印的每個應用程式, 核取 [損毀傾印**已啟用**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-299">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="6ff7e-300">返回此頁面以收集損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-300">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="6ff7e-301">可以[在 Visual Studio 中開啟傾印檔案以進行偵錯工具](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-301">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="6ff7e-302">檔案總管</span><span class="sxs-lookup"><span data-stu-id="6ff7e-302">File Explorer</span></span>

<span data-ttu-id="6ff7e-303">![Microsoft HoloLens 上 Windows 裝置入口網站中的檔案瀏覽器頁面](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-303">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-304">*Microsoft HoloLens 上 Windows 裝置入口網站中的檔案瀏覽器頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-304">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-305">使用 [檔案瀏覽器] 流覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-305">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="6ff7e-306">您可以針對從 Visual Studio 或裝置入口網站部署的應用程式, 使用 [檔] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-306">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="6ff7e-307">Kiosk 模式</span><span class="sxs-lookup"><span data-stu-id="6ff7e-307">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="6ff7e-308">Kiosk 模式僅適用于[Microsoft HoloLens 商業套件](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-308">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="6ff7e-309">如需透過 Windows 裝置入口網站啟用 kiosk 模式的最新指示, 請參閱 Windows IT Pro 中心的在[kiosk 模式中設定 HoloLens 一](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)文。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-309">Please check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="6ff7e-310">記錄</span><span class="sxs-lookup"><span data-stu-id="6ff7e-310">Logging</span></span>

<span data-ttu-id="6ff7e-311">![Microsoft HoloLens 上 Windows 裝置入口網站中的 [記錄] 頁面](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-311">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-312">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [記錄] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-312">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-313">管理 HoloLens 上 Windows (ETW) 的即時事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-313">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="6ff7e-314">勾選 [**隱藏提供者**] 僅顯示**事件**清單。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-314">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="6ff7e-315">**已註冊的提供者**:選取 ETW 提供者和追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-315">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="6ff7e-316">追蹤等級是下列其中一個值 ︰</span><span class="sxs-lookup"><span data-stu-id="6ff7e-316">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="6ff7e-317">異常結束或終止</span><span class="sxs-lookup"><span data-stu-id="6ff7e-317">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="6ff7e-318">嚴重錯誤</span><span class="sxs-lookup"><span data-stu-id="6ff7e-318">Severe errors</span></span>
   3. <span data-ttu-id="6ff7e-319">警告</span><span class="sxs-lookup"><span data-stu-id="6ff7e-319">Warnings</span></span>
   4. <span data-ttu-id="6ff7e-320">非錯誤警告</span><span class="sxs-lookup"><span data-stu-id="6ff7e-320">Non-error warnings</span></span>

<span data-ttu-id="6ff7e-321">按一下或點選 [啟用] 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-321">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="6ff7e-322">提供者已新增到 [啟用的提供者] 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-322">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="6ff7e-323">**自訂提供者**:選取自訂 ETW 提供者和追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-323">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="6ff7e-324">依 GUID 識別提供者。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-324">Identify the provider by its GUID.</span></span> <span data-ttu-id="6ff7e-325">不要在 GUID 中包含括號。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-325">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="6ff7e-326">**啟用的提供者**:列出已啟用的提供者。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-326">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="6ff7e-327">從下拉式清單選取提供者，然後按一下或點選 [停用] 以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-327">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="6ff7e-328">按一下或點選 [全部停止] 以暫停所有追蹤。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-328">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="6ff7e-329">**提供者歷程記錄**:顯示目前會話期間已啟用的 ETW 提供者。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-329">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="6ff7e-330">按一下或點選 [啟用] 以啟用已停用的提供者。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-330">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="6ff7e-331">按一下或點選 [清除] 以清除歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-331">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="6ff7e-332">**事件**:以資料表格式列出來自所選提供者的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-332">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="6ff7e-333">此表格會即時更新。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-333">This table is updated in real time.</span></span> <span data-ttu-id="6ff7e-334">在資料表下方, 按一下 [**清除**] 按鈕, 以刪除資料表中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-334">Beneath the table, click on the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="6ff7e-335">這不會停用任何提供者。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-335">This does not disable any providers.</span></span> <span data-ttu-id="6ff7e-336">您可以按一下 **\[儲存到檔案\]** ，將目前收集的 ETW 事件匯出到本機的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-336">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="6ff7e-337">**篩選器**:可讓您篩選識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-337">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="6ff7e-338">您可以將數個準則結合在一起:</span><span class="sxs-lookup"><span data-stu-id="6ff7e-338">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="6ff7e-339">針對套用至相同屬性事件的準則, 可以滿足其中任何一項準則。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-339">For criteria applying to the same property - events can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="6ff7e-340">適用于套用至不同屬性事件的準則必須滿足所有條件</span><span class="sxs-lookup"><span data-stu-id="6ff7e-340">For criteria applying to different property - events must satisfy all of the criteria</span></span>

<span data-ttu-id="6ff7e-341">例如, 您可以指定準則 *([工作名稱] 包含 [Foo] 或 [橫條]) 和 (文字包含 [錯誤] 或 [警告])*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-341">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="6ff7e-342">模擬</span><span class="sxs-lookup"><span data-stu-id="6ff7e-342">Simulation</span></span>

<span data-ttu-id="6ff7e-343">![Microsoft HoloLens 上 Windows 裝置入口網站中的模擬頁面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-343">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-344">*Microsoft HoloLens 上 Windows 裝置入口網站中的模擬頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-344">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-345">允許您記錄並播放輸入資料以進行測試。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-345">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="6ff7e-346">**Capture 室**:用來下載模擬的會議室檔案, 其中包含使用者周圍的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-346">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="6ff7e-347">為房間命名, 然後按一下 [ **Capture** ], 將資料儲存為電腦上的 xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-347">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="6ff7e-348">此房間檔案可以載入 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-348">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="6ff7e-349">**記錄**:檢查要記錄的資料流程、將記錄命名為, 然後按一下或按下 [**記錄**] 開始進行編碼。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-349">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="6ff7e-350">使用 HoloLens 執行動作, 然後按一下 [**停止**], 將資料儲存為電腦上的 xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-350">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="6ff7e-351">此檔案可以載入 HoloLens 模擬器或裝置。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-351">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="6ff7e-352">**播放**:按一下或點擊 **[上傳記錄**], 從您的電腦選取 xef 檔案, 並將資料傳送至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-352">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="6ff7e-353">**控制模式**:從下拉式清單中選取 [**預設**] 或 [**模擬**], 然後按一下或點擊 [**設定**] 按鈕, 以選取 HoloLens 上的模式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-353">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="6ff7e-354">選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-354">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="6ff7e-355">如果您切換到 [模擬]，您的 HoloLens 將不會對真實使用者做出回應，直到您切換回 [預設] 為止。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-355">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="6ff7e-356">網路功能</span><span class="sxs-lookup"><span data-stu-id="6ff7e-356">Networking</span></span>

<span data-ttu-id="6ff7e-357">![Microsoft HoloLens 上 Windows 裝置入口網站中的網路功能頁面](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-357">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-358">*Microsoft HoloLens 上 Windows 裝置入口網站中的網路功能頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-358">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-359">管理 HoloLens 上的 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-359">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="6ff7e-360">**WiFi 介面卡**:使用下拉式清單控制項選取 Wi-fi 介面卡和設定檔。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-360">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="6ff7e-361">按一下或點擊 **[連線]** 以使用選取的介面卡。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-361">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="6ff7e-362">**可用的網路**:列出 HoloLens 可以連接的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-362">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="6ff7e-363">按一下或點擊 [重新整理] 以更新清單。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-363">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="6ff7e-364">**IP**設定:顯示網路連線的 IP 位址和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-364">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="6ff7e-365">虛擬輸入</span><span class="sxs-lookup"><span data-stu-id="6ff7e-365">Virtual Input</span></span>

<span data-ttu-id="6ff7e-366">![Microsoft HoloLens 上 Windows 裝置入口網站中的虛擬輸入頁面](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6ff7e-366">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="6ff7e-367">*Microsoft HoloLens 上 Windows 裝置入口網站中的虛擬輸入頁面*</span><span class="sxs-lookup"><span data-stu-id="6ff7e-367">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6ff7e-368">從遠端電腦傳送鍵盤輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-368">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="6ff7e-369">按一下或點擊 [**虛擬鍵盤**] 底下的區域, 以啟用將按鍵傳送至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-369">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="6ff7e-370">在 [**輸入文字**] 文字方塊中輸入, 然後按一下或按 [**傳送**], 將按鍵傳送至使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-370">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="6ff7e-371">裝置入口網站 REST API</span><span class="sxs-lookup"><span data-stu-id="6ff7e-371">Device Portal REST API's</span></span>

<span data-ttu-id="6ff7e-372">裝置入口網站中的所有專案都是以[REST API](device-portal-api-reference.md)為基礎, 您可以選擇性地使用它來存取資料, 並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6ff7e-372">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
