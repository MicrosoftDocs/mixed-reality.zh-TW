---
title: 使用 Windows 裝置入口網站
description: 適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具，可協助您管理 HoloLens 並對應用程式進行優化和優化。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 裝置入口網站、HoloLens
ms.openlocfilehash: 43ecfead7d2882d3624809bc05184f74131b8594
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202718"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="6be73-106">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="6be73-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="6be73-107">功能</span><span class="sxs-lookup"><span data-stu-id="6be73-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="6be73-108"><a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="6be73-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="6be73-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6be73-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="6be73-110"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="6be73-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="6be73-111">Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="6be73-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="6be73-112">✔️</span><span class="sxs-lookup"><span data-stu-id="6be73-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6be73-113">✔️</span><span class="sxs-lookup"><span data-stu-id="6be73-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="6be73-114">適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6be73-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="6be73-115">Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。</span><span class="sxs-lookup"><span data-stu-id="6be73-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="6be73-116">裝置入口網站包含許多工具，可協助您管理 HoloLens 並對應用程式進行優化和優化。</span><span class="sxs-lookup"><span data-stu-id="6be73-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="6be73-117">本檔特別說明適用于 HoloLens 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6be73-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="6be73-118">若要使用適用于桌面的 Windows 裝置入口網站（包括 Windows Mixed Reality），請參閱[Windows 裝置入口網站總覽](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="6be73-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="6be73-119">設定 HoloLens 以使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="6be73-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="6be73-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="6be73-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="6be73-121">在 HoloLens （第1代）上執行 HoloLens2 或[Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)的[開始手勢](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)，以啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="6be73-121">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="6be73-122">看一下 [**設定**] 圖格，然後在 hololens （第1代）上執行 [[空中](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)操作] 手勢，或透過[觸碰或使用手光線](https://docs.microsoft.com/hololens/hololens2-basic-usage)在 hololens 2 上選取它。</span><span class="sxs-lookup"><span data-stu-id="6be73-122">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="6be73-123">選取 **\[更新\]** 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6be73-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="6be73-124">選取 **\[適用於開發人員\]** 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6be73-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="6be73-125">啟用 **\[開發人員模式\]** 。</span><span class="sxs-lookup"><span data-stu-id="6be73-125">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="6be73-126">[向下滾動](gaze-and-commit.md#composite-gestures)並啟用 [**裝置入口網站**]。</span><span class="sxs-lookup"><span data-stu-id="6be73-126">[Scroll down](gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="6be73-127">如果您要設定 Windows 裝置入口網站，讓您可以透過 USB 或 Wi-fi 將應用程式部署到此 HoloLens，請按一下 [**配對**] 以[產生配對 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="6be73-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="6be73-128">將 [設定] 應用程式保留在 [PIN] 快顯視窗中，直到您在第一次部署期間輸入 Visual Studio 的 PIN 為止。</span><span class="sxs-lookup"><span data-stu-id="6be73-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="6be73-130">透過 Wi-fi 連接</span><span class="sxs-lookup"><span data-stu-id="6be73-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="6be73-131">[將 HoloLens 連接至 wi-fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="6be73-131">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="6be73-132">查詢您裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6be73-132">Look up your device's IP address.</span></span>
   * <span data-ttu-id="6be73-133">在 [設定] 底下的裝置上尋找 IP 位址 **> 網路 & 網際網路 > wi-fi > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="6be73-133">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="6be73-134">從您電腦上的網頁瀏覽器，移至 HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS ></span><span class="sxs-lookup"><span data-stu-id="6be73-134">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="6be73-135">瀏覽器會顯示下列訊息：「此網站的安全性憑證有問題」。</span><span class="sxs-lookup"><span data-stu-id="6be73-135">The browser will display the following message: "There’s a problem with this website’s security certificate".</span></span> <span data-ttu-id="6be73-136">這是因為核發給 Device Portal 的憑證是測試憑證。</span><span class="sxs-lookup"><span data-stu-id="6be73-136">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="6be73-137">您可以暫時略過這個憑證錯誤並繼續。</span><span class="sxs-lookup"><span data-stu-id="6be73-137">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="6be73-138">透過 USB 連接</span><span class="sxs-lookup"><span data-stu-id="6be73-138">Connecting over USB</span></span>

1. <span data-ttu-id="6be73-139">[安裝工具](install-the-tools.md)，以確定您已在電腦上安裝 Windows 10 開發人員工具來執行 Visual Studio Update 1。</span><span class="sxs-lookup"><span data-stu-id="6be73-139">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="6be73-140">這將能啟用 USB 連線能力。</span><span class="sxs-lookup"><span data-stu-id="6be73-140">This enables USB connectivity.</span></span>
2. <span data-ttu-id="6be73-141">使用 hololens （第1代）的微 USB 纜線或 HoloLens 2 的 USB-C，將您的 HoloLens 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="6be73-141">Connect your HoloLens to your PC with a micro-USB cable for HoloLens (1st Gen) or USB-C for HoloLens 2.</span></span>
3. <span data-ttu-id="6be73-142">從您電腦上的網頁瀏覽器，移至 [ [https://127.0.0.1:10080](https://127.0.0.1:10080)]。</span><span class="sxs-lookup"><span data-stu-id="6be73-142">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="6be73-143">連接到模擬器</span><span class="sxs-lookup"><span data-stu-id="6be73-143">Connecting to an emulator</span></span>

<span data-ttu-id="6be73-144">您也可以透過模擬器使用 Device Portal。</span><span class="sxs-lookup"><span data-stu-id="6be73-144">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="6be73-145">若要連接到裝置入口網站，請使用[工具列](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="6be73-145">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="6be73-146">按一下此圖示： ![開啟 [裝置入口網站] 圖示](images/emulator-deviceportal.png)**開啟 [裝置入口網站**]：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6be73-146">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="6be73-147">建立使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="6be73-147">Creating a Username and Password</span></span>

<span data-ttu-id="6be73-148">![設定 Windows 裝置入口網站](images/windows-device-portal-credentials-reset-page-1000px.png) 的存取權</span><span class="sxs-lookup"><span data-stu-id="6be73-148">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-149">*設定 Windows 裝置入口網站的存取權*</span><span class="sxs-lookup"><span data-stu-id="6be73-149">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="6be73-150">首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6be73-150">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="6be73-151">在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6be73-151">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="6be73-152">[設定存取] 頁面將會開啟。</span><span class="sxs-lookup"><span data-stu-id="6be73-152">The Set up access page opens.</span></span>
2. <span data-ttu-id="6be73-153">按一下或點擊 [**要求 pin** ]，並查看 HoloLens 顯示以取得產生的 pin。</span><span class="sxs-lookup"><span data-stu-id="6be73-153">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="6be73-154">在 [**您的裝置上顯示的 pin** ] 文字方塊中輸入 pin。</span><span class="sxs-lookup"><span data-stu-id="6be73-154">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="6be73-155">輸入您會用來連線到 Device Portal 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6be73-155">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="6be73-156">它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6be73-156">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="6be73-157">輸入密碼並確認它。</span><span class="sxs-lookup"><span data-stu-id="6be73-157">Enter a password and confirm it.</span></span> <span data-ttu-id="6be73-158">密碼長度必須至少為七個字元。</span><span class="sxs-lookup"><span data-stu-id="6be73-158">The password must be at least seven characters in length.</span></span> <span data-ttu-id="6be73-159">它並不需要是 MSA 或網域密碼。</span><span class="sxs-lookup"><span data-stu-id="6be73-159">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="6be73-160">按一下 [**配對**] 以連線至 HoloLens 上的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="6be73-160">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="6be73-161">如果您想要隨時變更此使用者名稱或密碼，您可以流覽至： HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.，藉此重複此程式。</span><span class="sxs-lookup"><span data-stu-id="6be73-161">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="6be73-162">安全性憑證</span><span class="sxs-lookup"><span data-stu-id="6be73-162">Security certificate</span></span>

<span data-ttu-id="6be73-163">如果您在瀏覽器中看到「憑證錯誤」，您可以藉由建立與裝置的信任關係來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="6be73-163">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="6be73-164">每個 HoloLens 都會為其 SSL 連線產生唯一的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="6be73-164">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="6be73-165">根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。</span><span class="sxs-lookup"><span data-stu-id="6be73-165">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="6be73-166">藉由從您的 HoloLens 下載此憑證 (透過 USB 或您信任的 Wi-Fi 網路)，並在電腦上信任它，您便能安全地連線到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6be73-166">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="6be73-167">**請確定您使用的是安全的網路（USB 或您信任的 Wi-fi 網路）。**</span><span class="sxs-lookup"><span data-stu-id="6be73-167">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="6be73-168">從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。</span><span class="sxs-lookup"><span data-stu-id="6be73-168">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="6be73-169">流覽至： HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="6be73-169">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="6be73-170">開啟 [系統 > 喜好設定] 的節點。</span><span class="sxs-lookup"><span data-stu-id="6be73-170">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="6be73-171">向下流覽至 [裝置安全性]，按一下 [下載此裝置的憑證] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6be73-171">Scroll down to Device Security, click the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="6be73-172">將憑證安裝在您電腦上的「受信任的根憑證授權」存放區中。</span><span class="sxs-lookup"><span data-stu-id="6be73-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="6be73-173">從 [Windows] 功能表中，輸入：管理電腦憑證並啟動 applet。</span><span class="sxs-lookup"><span data-stu-id="6be73-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="6be73-174">展開 [**信任的根憑證授權**單位] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be73-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="6be73-175">按一下 [**憑證**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be73-175">Click the **Certificates** folder.</span></span>
   * <span data-ttu-id="6be73-176">從 [動作] 功能表中，選取：[所有工作] &gt; [匯入]...</span><span class="sxs-lookup"><span data-stu-id="6be73-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="6be73-177">使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="6be73-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="6be73-178">重新啟動瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6be73-178">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="6be73-179">只有裝置才會信任此憑證，而使用者必須在裝置已閃時再次執行此程式。</span><span class="sxs-lookup"><span data-stu-id="6be73-179">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>


## <a name="device-portal-pages"></a><span data-ttu-id="6be73-180">Device Portal 頁面</span><span class="sxs-lookup"><span data-stu-id="6be73-180">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="6be73-181">首頁</span><span class="sxs-lookup"><span data-stu-id="6be73-181">Home</span></span>

<span data-ttu-id="6be73-182">![Windows 裝置入口網站首頁上的 Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-182">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-183">*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*</span><span class="sxs-lookup"><span data-stu-id="6be73-183">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-184">您的 Device Portal 工作階段從首頁開始。</span><span class="sxs-lookup"><span data-stu-id="6be73-184">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="6be73-185">從首頁左側的瀏覽列中存取其他頁面。</span><span class="sxs-lookup"><span data-stu-id="6be73-185">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="6be73-186">頁面頂端的工具列能讓您存取常用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="6be73-186">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="6be73-187">**線上**：指出裝置是否已連線到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="6be73-187">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="6be73-188">**關機**：關閉裝置。</span><span class="sxs-lookup"><span data-stu-id="6be73-188">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="6be73-189">**重新啟動**：關閉裝置電源並重新開啟。</span><span class="sxs-lookup"><span data-stu-id="6be73-189">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="6be73-190">**安全性**：開啟 [裝置安全性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6be73-190">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="6be73-191">**冷卻**：指出裝置的溫度。</span><span class="sxs-lookup"><span data-stu-id="6be73-191">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="6be73-192">**A/C**：指出裝置是否已插上電源並且正在充電。</span><span class="sxs-lookup"><span data-stu-id="6be73-192">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="6be73-193">**說明**：開啟 REST 介面文件頁面。</span><span class="sxs-lookup"><span data-stu-id="6be73-193">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="6be73-194">首頁將顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6be73-194">The home page shows the following info:</span></span>
* <span data-ttu-id="6be73-195">**裝置狀態：** 監視裝置的健全狀況，並回報重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="6be73-195">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="6be73-196">**Windows 資訊：** 顯示 HoloLens 的名稱和目前安裝的 windows 版本。</span><span class="sxs-lookup"><span data-stu-id="6be73-196">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="6be73-197">**\[喜好設定\]** 區段包含下列設定：</span><span class="sxs-lookup"><span data-stu-id="6be73-197">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="6be73-198">**IPD**：設定瞳孔間距 (IPD)，這是使用者雙眼注視前方時，兩個瞳孔中心點之間的距離 (以公釐為單位)。</span><span class="sxs-lookup"><span data-stu-id="6be73-198">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="6be73-199">此設定會立即生效。</span><span class="sxs-lookup"><span data-stu-id="6be73-199">The setting takes effect immediately.</span></span> <span data-ttu-id="6be73-200">預設值會在您設定裝置時自動計算。</span><span class="sxs-lookup"><span data-stu-id="6be73-200">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="6be73-201">**裝置名稱**：為 HoloLens 指派名稱。</span><span class="sxs-lookup"><span data-stu-id="6be73-201">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="6be73-202">在變更此值之後，必須重新啟動裝置才能生效。</span><span class="sxs-lookup"><span data-stu-id="6be73-202">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="6be73-203">按一下 [**儲存**] 之後，對話方塊會詢問您是否要立即重新開機裝置，或稍後重新開機。</span><span class="sxs-lookup"><span data-stu-id="6be73-203">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="6be73-204">**睡眠設定**：設定裝置在接上電源及使用電池的情況下，在進入睡眠之前所需等待的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6be73-204">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="6be73-205">3D 檢視</span><span class="sxs-lookup"><span data-stu-id="6be73-205">3D View</span></span>

<span data-ttu-id="6be73-206">在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![3D 視圖頁面](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-206">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="6be73-207">*Microsoft HoloLens 上 Windows 裝置入口網站中的 3D View 頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-207">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-208">使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。</span><span class="sxs-lookup"><span data-stu-id="6be73-208">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="6be73-209">使用滑鼠來瀏覽檢視：</span><span class="sxs-lookup"><span data-stu-id="6be73-209">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="6be73-210">旋轉：按滑鼠左鍵 + 滑鼠;</span><span class="sxs-lookup"><span data-stu-id="6be73-210">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="6be73-211">Pan：以滑鼠右鍵按一下滑鼠;</span><span class="sxs-lookup"><span data-stu-id="6be73-211">Pan: right click + mouse;</span></span>
* <span data-ttu-id="6be73-212">Zoom：滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="6be73-212">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="6be73-213">**追蹤選項**</span><span class="sxs-lookup"><span data-stu-id="6be73-213">**Tracking options**</span></span>
   * <span data-ttu-id="6be73-214">藉由勾選 [**強制視覺效果追蹤**]，開啟連續視覺效果追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-214">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="6be73-215">[**暫停**] 會停止視覺效果追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-215">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="6be73-216">**視圖選項**：在3d 視圖上設定選項：</span><span class="sxs-lookup"><span data-stu-id="6be73-216">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="6be73-217">**追蹤**：指出視覺效果追蹤是否作用中。</span><span class="sxs-lookup"><span data-stu-id="6be73-217">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="6be73-218">**顯示地板**：顯示方格的地板平面。</span><span class="sxs-lookup"><span data-stu-id="6be73-218">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="6be73-219">**顯示範圍**：顯示檢視範圍。</span><span class="sxs-lookup"><span data-stu-id="6be73-219">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="6be73-220">**顯示穩定平面**：顯示 HoloLens 用來穩定動態的平面。</span><span class="sxs-lookup"><span data-stu-id="6be73-220">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="6be73-221">**顯示網格**：顯示代表您周圍的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6be73-221">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="6be73-222">**顯示空間錨點**：顯示作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="6be73-222">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="6be73-223">您必須按一下 [更新] 按鈕，才能取得並重新整理錨點。</span><span class="sxs-lookup"><span data-stu-id="6be73-223">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="6be73-224">**顯示詳細資料**：隨著下列數據變更，即時顯示雙手位置、頭部旋轉四元數，以及裝置原點向量。</span><span class="sxs-lookup"><span data-stu-id="6be73-224">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="6be73-225">**全螢幕按鈕**：以全螢幕模式顯示 3D 檢視。</span><span class="sxs-lookup"><span data-stu-id="6be73-225">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="6be73-226">按下 ESC 以離開全螢幕檢視。</span><span class="sxs-lookup"><span data-stu-id="6be73-226">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="6be73-227">**表面重建**：按一下或點擊 [**更新**]，以顯示裝置的最新空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6be73-227">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="6be73-228">完整階段可能需要一些時間才能完成（最多幾秒鐘）。</span><span class="sxs-lookup"><span data-stu-id="6be73-228">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="6be73-229">網格不會在3D 視圖中自動更新，您必須手動按一下 [**更新**]，從裝置取得最新的網格。</span><span class="sxs-lookup"><span data-stu-id="6be73-229">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="6be73-230">按一下 [**儲存**]，將目前的空間對應網格儲存為電腦上的 obj 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-230">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="6be73-231">**空間錨點**：按一下 [更新] 以顯示或更新作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="6be73-231">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="6be73-232">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="6be73-232">Mixed Reality Capture</span></span>

<span data-ttu-id="6be73-233">在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![混合現實捕捉頁面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-233">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-234">*Microsoft HoloLens 上 Windows 裝置入口網站中的混合現實 Capture 頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-234">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-235">使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-235">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="6be73-236">**設定**：藉由檢查下列設定來控制所捕捉的媒體資料流程：</span><span class="sxs-lookup"><span data-stu-id="6be73-236">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="6be73-237">**全息影像**：在影片串流中捕捉全像攝影內容。</span><span class="sxs-lookup"><span data-stu-id="6be73-237">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="6be73-238">全像投影是以單聲道進行轉譯，而非立體聲。</span><span class="sxs-lookup"><span data-stu-id="6be73-238">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="6be73-239">**PV 相機**：擷取來自相片/視訊攝影機的視訊串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-239">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="6be73-240">**麥克風音訊**：擷取來自麥克風陣列的音訊。</span><span class="sxs-lookup"><span data-stu-id="6be73-240">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="6be73-241">**App 音訊**：擷取來自目前正在執行之 app 的音訊。</span><span class="sxs-lookup"><span data-stu-id="6be73-241">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="6be73-242">**從相機**轉譯：當執行中的[應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)（僅限 HoloLens 2）時，將捕捉從相片/攝影機的角度對齊。</span><span class="sxs-lookup"><span data-stu-id="6be73-242">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="6be73-243">**即時預覽品質**：選取即時預覽的螢幕解析度、畫面播放速率，以及串流速率。</span><span class="sxs-lookup"><span data-stu-id="6be73-243">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="6be73-244">按一下或點擊 [**即時預覽**] 按鈕以顯示 capture 串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-244">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="6be73-245">[**停止即時預覽**] 會停止 capture 串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-245">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="6be73-246">按一下或按下 [**記錄**]，以使用指定的設定開始記錄混合現實串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-246">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="6be73-247">[**停止錄製**] 會結束錄製並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="6be73-247">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="6be73-248">按一下或點擊 [**拍攝相片**]，從 capture 串流拍攝靜止的影像。</span><span class="sxs-lookup"><span data-stu-id="6be73-248">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="6be73-249">**視訊與相片**：顯示在裝置上拍攝之視訊和相片擷取的清單。</span><span class="sxs-lookup"><span data-stu-id="6be73-249">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="6be73-250">[同時 MRC 的限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)如下：</span><span class="sxs-lookup"><span data-stu-id="6be73-250">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="6be73-251">如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機，影片錄製將會停止。</span><span class="sxs-lookup"><span data-stu-id="6be73-251">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="6be73-252">如果應用程式存取具有 SharedReadOnly 模式的相片/攝影機，則 HoloLens 2 不會停止錄製影片。</span><span class="sxs-lookup"><span data-stu-id="6be73-252">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="6be73-253">如果應用程式正在使用相片/攝影機，Windows 裝置入口網站就能夠拍攝相片或錄製影片。</span><span class="sxs-lookup"><span data-stu-id="6be73-253">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="6be73-254">即時串流：</span><span class="sxs-lookup"><span data-stu-id="6be73-254">Live streaming:</span></span>
>   * <span data-ttu-id="6be73-255">HoloLens （第1代）可防止應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="6be73-255">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="6be73-256">如果應用程式正在使用相片/攝影機，HoloLens （第1代）將無法即時串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-256">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="6be73-257">當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時，HoloLens 2 會自動停止即時串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-257">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="6be73-258">當應用程式主動使用 PV 攝影機時，HoloLens 2 可以啟動即時串流。</span><span class="sxs-lookup"><span data-stu-id="6be73-258">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="6be73-259">效能追蹤</span><span class="sxs-lookup"><span data-stu-id="6be73-259">Performance Tracing</span></span>

<span data-ttu-id="6be73-260">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![效能追蹤 頁面](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-260">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-261">*Microsoft HoloLens 上 Windows 裝置入口網站中的效能追蹤頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-261">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-262">從 HoloLens 捕獲[Windows 效能錄製](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)器（WPR）追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-262">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="6be73-263">**可用的設定檔**︰從下拉式清單選取 WPR 設定檔，然後按一下或點選 **\[開始\]** 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-263">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="6be73-264">**自訂設定檔**︰按一下或點選 **\[瀏覽\]** ，以從您的電腦選擇 WPR 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6be73-264">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="6be73-265">按一下或點選 **\[上傳並開始\]** 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-265">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="6be73-266">若要停止追蹤，請按一下 [停止] 連結。</span><span class="sxs-lookup"><span data-stu-id="6be73-266">To stop the trace, click the stop link.</span></span> <span data-ttu-id="6be73-267">在追蹤檔案下載完成之前，請停留在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="6be73-267">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="6be73-268">擷取的 ETL 檔案可以在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中開啟以進行分析。</span><span class="sxs-lookup"><span data-stu-id="6be73-268">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="6be73-269">處理序</span><span class="sxs-lookup"><span data-stu-id="6be73-269">Processes</span></span>

<span data-ttu-id="6be73-270">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![處理常式 頁面](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-270">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-271">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [進程] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-271">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-272">顯示有關目前正在執行之處理程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6be73-272">Shows details about currently running processes.</span></span> <span data-ttu-id="6be73-273">這包括 App 與系統處理程序。</span><span class="sxs-lookup"><span data-stu-id="6be73-273">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="6be73-274">系統效能</span><span class="sxs-lookup"><span data-stu-id="6be73-274">System Performance</span></span>

<span data-ttu-id="6be73-275">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![系統效能 頁面](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-275">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-276">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [系統效能] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-276">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-277">顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。</span><span class="sxs-lookup"><span data-stu-id="6be73-277">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="6be73-278">下列為可用的衡量標準：</span><span class="sxs-lookup"><span data-stu-id="6be73-278">These are the available metrics:</span></span>
* <span data-ttu-id="6be73-279">**SoC 電源**：系統單晶片電源瞬間使用率 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="6be73-279">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="6be73-280">**系統電源**：系統電源瞬間使用率 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="6be73-280">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="6be73-281">**畫面播放速率**：每秒的畫面格數、每秒遺失的 VBlanks 數，以及連續遺失的 VBlanks 數。</span><span class="sxs-lookup"><span data-stu-id="6be73-281">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="6be73-282">**GPU**：GPU 引擎使用率、可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="6be73-282">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="6be73-283">**CPU**：可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="6be73-283">**CPU**: percent of total available</span></span>
* <span data-ttu-id="6be73-284">**I/O**：讀取與寫入</span><span class="sxs-lookup"><span data-stu-id="6be73-284">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="6be73-285">**網路**︰已接收與已傳送</span><span class="sxs-lookup"><span data-stu-id="6be73-285">**Network**: Received and sent</span></span>
* <span data-ttu-id="6be73-286">**記憶體**：總計、使用中、已認可、已分頁和未分頁</span><span class="sxs-lookup"><span data-stu-id="6be73-286">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="6be73-287">應用程式</span><span class="sxs-lookup"><span data-stu-id="6be73-287">Apps</span></span>

<span data-ttu-id="6be73-288">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![應用程式 頁面](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-288">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-289">*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-289">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-290">管理安裝在 HoloLens 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6be73-290">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="6be73-291">**已安裝的 App**︰移除及啟動 App。</span><span class="sxs-lookup"><span data-stu-id="6be73-291">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="6be73-292">**執行中 App**︰列出目前的執行中 App。</span><span class="sxs-lookup"><span data-stu-id="6be73-292">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="6be73-293">**安裝應用程式**：從電腦/網路上的資料夾選取要安裝的應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="6be73-293">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="6be73-294">**相依性**︰新增將要安裝之 app 的相依性。</span><span class="sxs-lookup"><span data-stu-id="6be73-294">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="6be73-295">**部署**：將選取的應用程式 + 相依性部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6be73-295">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="6be73-296">應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="6be73-296">App Crash Dumps</span></span>

<span data-ttu-id="6be73-297">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![應用程式損毀傾印頁面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-297">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-298">*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式損毀傾印頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-298">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-299">此頁面可讓您收集側載 App 的損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="6be73-299">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="6be73-300">針對您要收集損毀傾印的每個應用程式，核取 [損毀傾印**已啟用**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6be73-300">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="6be73-301">返回此頁面以收集損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="6be73-301">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="6be73-302">可以[在 Visual Studio 中開啟傾印檔案以進行偵錯工具](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6be73-302">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="6be73-303">檔案總管</span><span class="sxs-lookup"><span data-stu-id="6be73-303">File Explorer</span></span>

<span data-ttu-id="6be73-304">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![檔案瀏覽器 頁面](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-304">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="6be73-305">*Microsoft HoloLens 上 Windows 裝置入口網站中的檔案瀏覽器頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-305">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-306">使用 [檔案瀏覽器] 流覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-306">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="6be73-307">您可以針對從 Visual Studio 或裝置入口網站部署的應用程式，使用 [檔] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-307">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="6be73-308">Kiosk 模式</span><span class="sxs-lookup"><span data-stu-id="6be73-308">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="6be73-309">Kiosk 模式僅適用于[Microsoft HoloLens 商業套件](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="6be73-309">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="6be73-310">如需透過 Windows 裝置入口網站啟用 kiosk 模式的最新指示，請參閱 Windows IT Pro 中心的在[kiosk 模式中設定 HoloLens 一](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)文。</span><span class="sxs-lookup"><span data-stu-id="6be73-310">Check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="6be73-311">記錄</span><span class="sxs-lookup"><span data-stu-id="6be73-311">Logging</span></span>

<span data-ttu-id="6be73-312">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![記錄頁面](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-312">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-313">*Microsoft HoloLens 上 Windows 裝置入口網站中的 [記錄] 頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-313">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-314">管理 HoloLens 上 Windows （ETW）的即時事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-314">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="6be73-315">勾選 [**隱藏提供者**] 僅顯示**事件**清單。</span><span class="sxs-lookup"><span data-stu-id="6be73-315">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="6be73-316">**已登錄的提供者**︰選取 ETW 提供者與追蹤等級。</span><span class="sxs-lookup"><span data-stu-id="6be73-316">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="6be73-317">追蹤等級是下列其中一個值 ︰</span><span class="sxs-lookup"><span data-stu-id="6be73-317">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="6be73-318">異常結束或終止</span><span class="sxs-lookup"><span data-stu-id="6be73-318">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="6be73-319">嚴重錯誤</span><span class="sxs-lookup"><span data-stu-id="6be73-319">Severe errors</span></span>
   3. <span data-ttu-id="6be73-320">警告</span><span class="sxs-lookup"><span data-stu-id="6be73-320">Warnings</span></span>
   4. <span data-ttu-id="6be73-321">非錯誤警告</span><span class="sxs-lookup"><span data-stu-id="6be73-321">Non-error warnings</span></span>

<span data-ttu-id="6be73-322">按一下或點選 **\[啟用\]** 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-322">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="6be73-323">提供者已新增到 **\[啟用的提供者\]** 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="6be73-323">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="6be73-324">**自訂提供者**︰選取自訂 ETW 提供者與追蹤等級。</span><span class="sxs-lookup"><span data-stu-id="6be73-324">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="6be73-325">依 GUID 識別提供者。</span><span class="sxs-lookup"><span data-stu-id="6be73-325">Identify the provider by its GUID.</span></span> <span data-ttu-id="6be73-326">不要在 GUID 中包含括號。</span><span class="sxs-lookup"><span data-stu-id="6be73-326">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="6be73-327">**啟用的提供者**：列出已啟用的提供者。</span><span class="sxs-lookup"><span data-stu-id="6be73-327">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="6be73-328">從下拉式清單選取提供者，然後按一下或點選 **\[停用\]** 以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-328">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="6be73-329">按一下或點選 **\[全部停止\]** 以暫停所有追蹤。</span><span class="sxs-lookup"><span data-stu-id="6be73-329">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="6be73-330">**提供者歷程記錄**︰顯示目前工作階段期間已啟用的 ETW 提供者。</span><span class="sxs-lookup"><span data-stu-id="6be73-330">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="6be73-331">按一下或點選 **\[啟用\]** 以啟用已停用的提供者。</span><span class="sxs-lookup"><span data-stu-id="6be73-331">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="6be73-332">按一下或點選 **\[清除\]** 以清除歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="6be73-332">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="6be73-333">**事件**︰以表格格式列出所選提供者的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6be73-333">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="6be73-334">此表格會即時更新。</span><span class="sxs-lookup"><span data-stu-id="6be73-334">This table is updated in real time.</span></span> <span data-ttu-id="6be73-335">在表格下方，按一下 **\[清除\]** 按鈕以刪除表格中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6be73-335">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="6be73-336">這不會停用任何提供者。</span><span class="sxs-lookup"><span data-stu-id="6be73-336">This does not disable any providers.</span></span> <span data-ttu-id="6be73-337">您可以按一下 **\[儲存到檔案\]** ，將目前收集的 ETW 事件匯出到本機的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-337">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="6be73-338">**篩選**：可讓您篩選識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6be73-338">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="6be73-339">您可以將數個準則結合在一起：</span><span class="sxs-lookup"><span data-stu-id="6be73-339">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="6be73-340">針對套用至相同屬性的準則，會顯示可滿足任一準則的事件。</span><span class="sxs-lookup"><span data-stu-id="6be73-340">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="6be73-341">針對套用至不同屬性的準則，事件必須滿足所有條件</span><span class="sxs-lookup"><span data-stu-id="6be73-341">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="6be73-342">例如，您可以指定準則 *（[工作名稱] 包含 [Foo] 或 [橫條]）和（文字包含 [錯誤] 或 [警告]）*</span><span class="sxs-lookup"><span data-stu-id="6be73-342">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="6be73-343">模擬</span><span class="sxs-lookup"><span data-stu-id="6be73-343">Simulation</span></span>

<span data-ttu-id="6be73-344">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![模擬 頁面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-344">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-345">*Microsoft HoloLens 上 Windows 裝置入口網站中的模擬頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-345">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-346">允許您記錄並播放輸入資料以進行測試。</span><span class="sxs-lookup"><span data-stu-id="6be73-346">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="6be73-347">**擷取房間**：用來下載模擬的房間檔案，其中包含針對使用者周遭環境的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="6be73-347">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="6be73-348">為房間命名，然後按一下 [ **Capture** ]，將資料儲存為電腦上的 xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-348">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="6be73-349">此房間檔案可以載入 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="6be73-349">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="6be73-350">**錄製**：請檢查要記錄的資料流程、將記錄命名為，然後按一下或按下 [**記錄**] 以開始進行編碼。</span><span class="sxs-lookup"><span data-stu-id="6be73-350">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="6be73-351">使用 HoloLens 執行動作，然後按一下 [**停止**]，將資料儲存為電腦上的 xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be73-351">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="6be73-352">此檔案可以載入 HoloLens 模擬器或裝置。</span><span class="sxs-lookup"><span data-stu-id="6be73-352">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="6be73-353">**播放**：按一下或點擊 **[上傳記錄**]，從您的電腦選取 xef 檔案，並將資料傳送至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6be73-353">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="6be73-354">**控制模式**：從下拉式清單中選取 [**預設**] 或 [**模擬**]，然後按一下或點擊 [**設定**] 按鈕，以選取 HoloLens 上的模式。</span><span class="sxs-lookup"><span data-stu-id="6be73-354">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="6be73-355">選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。</span><span class="sxs-lookup"><span data-stu-id="6be73-355">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="6be73-356">如果您切換到 [模擬]，您的 HoloLens 將不會對真實使用者做出回應，直到您切換回 [預設] 為止。</span><span class="sxs-lookup"><span data-stu-id="6be73-356">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="6be73-357">網路功能</span><span class="sxs-lookup"><span data-stu-id="6be73-357">Networking</span></span>

<span data-ttu-id="6be73-358">Microsoft HoloLens 上 Windows 裝置入口網站中的 ![網路功能 頁面](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-358">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-359">*Microsoft HoloLens 上 Windows 裝置入口網站中的網路功能頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-359">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-360">管理 HoloLens 上的 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="6be73-360">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="6be73-361">**WiFi 介面卡**：使用下拉式清單控制項選取 wi-fi 介面卡和設定檔。</span><span class="sxs-lookup"><span data-stu-id="6be73-361">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="6be73-362">按一下或點擊 **[連線]** 以使用選取的介面卡。</span><span class="sxs-lookup"><span data-stu-id="6be73-362">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="6be73-363">**可用的網路**：列出 HoloLens 可以連接的 wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="6be73-363">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="6be73-364">按一下**或點擊 [** 重新整理] 以更新清單。</span><span class="sxs-lookup"><span data-stu-id="6be73-364">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="6be73-365">**Ip**設定：顯示 ip 位址和網路連線的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6be73-365">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="6be73-366">虛擬輸入</span><span class="sxs-lookup"><span data-stu-id="6be73-366">Virtual Input</span></span>

<span data-ttu-id="6be73-367">在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![虛擬輸入頁面](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6be73-367">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="6be73-368">*Microsoft HoloLens 上 Windows 裝置入口網站中的虛擬輸入頁面*</span><span class="sxs-lookup"><span data-stu-id="6be73-368">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="6be73-369">從遠端電腦傳送鍵盤輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6be73-369">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="6be73-370">按一下或點擊 [**虛擬鍵盤**] 底下的區域，以啟用將按鍵傳送至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6be73-370">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="6be73-371">在 [**輸入文字**] 文字方塊中輸入，然後按一下或按 [**傳送**]，將按鍵傳送至使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6be73-371">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="6be73-372">裝置入口網站 REST API</span><span class="sxs-lookup"><span data-stu-id="6be73-372">Device Portal REST API's</span></span>

<span data-ttu-id="6be73-373">裝置入口網站中的所有專案都是以[REST API](device-portal-api-reference.md)為基礎，您可以選擇性地使用它來存取資料，並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="6be73-373">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
