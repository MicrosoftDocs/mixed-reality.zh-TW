---
title: 使用 Windows 裝置入口網站
description: HoloLens 的 Windows 裝置入口網站能讓您從遠端透 Wi-Fi 或 USB 來設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具，可協助您管理 HoloLens，並對應用程式進行偵錯及最佳化。
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 裝置入口網站, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 9cd9b33fed12802e5b41afa3fee850356911a989
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278026"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="e13aa-106">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="e13aa-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="e13aa-107">功能</span><span class="sxs-lookup"><span data-stu-id="e13aa-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e13aa-108"><a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="e13aa-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e13aa-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e13aa-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="e13aa-110"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="e13aa-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e13aa-111">Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="e13aa-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="e13aa-112">✔️</span><span class="sxs-lookup"><span data-stu-id="e13aa-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e13aa-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e13aa-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="e13aa-114">HoloLens 的 Windows 裝置入口網站能讓您從遠端透 Wi-Fi 或 USB 來設定及管理您的裝置。</span><span class="sxs-lookup"><span data-stu-id="e13aa-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="e13aa-115">Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。</span><span class="sxs-lookup"><span data-stu-id="e13aa-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="e13aa-116">裝置入口網站包含許多工具，可協助您管理 HoloLens，並對應用程式進行偵錯及最佳化。</span><span class="sxs-lookup"><span data-stu-id="e13aa-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="e13aa-117">本文件特別說明適用於 HoloLens 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="e13aa-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="e13aa-118">若要使用適用於傳統型 Windows 裝置入口網站 (包括 Windows Mixed Reality)，請參閱 [Windows 裝置入口網站概觀](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="e13aa-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="e13aa-119">設定 HoloLens 以使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="e13aa-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="e13aa-120">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="e13aa-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="e13aa-121">執行 HoloLens2 的 [開始手勢](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)或 HoloLens (第 1 代) 的[綻開](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="e13aa-121">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="e13aa-122">看一下 [設定]  磚，然後執行 HoloLens (第 1 代) 的[空中點選](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手勢，或是在 HoloLens 2 上[觸碰或使用手部射線](https://docs.microsoft.com/hololens/hololens2-basic-usage)進行選取。</span><span class="sxs-lookup"><span data-stu-id="e13aa-122">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="e13aa-123">選取 [更新]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="e13aa-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="e13aa-124">選取 [適用於開發人員]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="e13aa-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="e13aa-125">啟用 [開發人員模式]  。</span><span class="sxs-lookup"><span data-stu-id="e13aa-125">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="e13aa-126">[向下捲動](gaze-and-commit.md#composite-gestures)並啟用**裝置入口網站**。</span><span class="sxs-lookup"><span data-stu-id="e13aa-126">[Scroll down](gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="e13aa-127">如果您要設定 Windows 裝置入口網站，以便透過 USB 或 Wi-Fi 將應用程式部署到此 HoloLens，請按一下 [配對]  以[產生配對 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="e13aa-128">將 [設定] 應用程式保留在 [PIN] 快顯視窗中，直到您在第一次部署期間，將 PIN 輸入 Visual Studio 為止。</span><span class="sxs-lookup"><span data-stu-id="e13aa-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="e13aa-130">透過 Wi-Fi 連線</span><span class="sxs-lookup"><span data-stu-id="e13aa-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="e13aa-131">[將您的 HoloLens 連線到 Wi-Fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-131">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="e13aa-132">尋找裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e13aa-132">Look up your device's IP address.</span></span>
   * <span data-ttu-id="e13aa-133">在裝置上的 [設定] > [網路和網際網路] > [Wi-Fi] > [進階選項]  下尋找 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e13aa-133">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="e13aa-134">從您電腦上的網頁瀏覽器，移至 https://<YOUR_HOLOLENS_IP_ADDRESS></span><span class="sxs-lookup"><span data-stu-id="e13aa-134">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="e13aa-135">瀏覽器將會顯示下列訊息：「此網站的安全性憑證有問題」。</span><span class="sxs-lookup"><span data-stu-id="e13aa-135">The browser will display the following message: "There's a problem with this website's security certificate".</span></span> <span data-ttu-id="e13aa-136">這是因為核發給 Device Portal 的憑證是測試憑證。</span><span class="sxs-lookup"><span data-stu-id="e13aa-136">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="e13aa-137">您可以暫時略過這個憑證錯誤並繼續。</span><span class="sxs-lookup"><span data-stu-id="e13aa-137">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="e13aa-138">透過 USB 連線</span><span class="sxs-lookup"><span data-stu-id="e13aa-138">Connecting over USB</span></span>

1. <span data-ttu-id="e13aa-139">[安裝工具](install-the-tools.md)以確保您擁有 Visual Studio Update 1，並在電腦上安裝 Windows 10 開發人員工具。</span><span class="sxs-lookup"><span data-stu-id="e13aa-139">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="e13aa-140">這將能啟用 USB 連線能力。</span><span class="sxs-lookup"><span data-stu-id="e13aa-140">This enables USB connectivity.</span></span>
2. <span data-ttu-id="e13aa-141">透過 Micro-USB 纜線將 HoloLens (第 1 代) 的 HoloLens 與電腦連線，或透過 USB-C 將 HoloLens 2 的 HoloLens 與電腦連線。</span><span class="sxs-lookup"><span data-stu-id="e13aa-141">Connect your HoloLens to your PC with a micro-USB cable for HoloLens (1st Gen) or USB-C for HoloLens 2.</span></span>
3. <span data-ttu-id="e13aa-142">從您電腦上的網頁瀏覽器，移至 [https://127.0.0.1:10080](https://127.0.0.1:10080)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-142">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="e13aa-143">連線到模擬器</span><span class="sxs-lookup"><span data-stu-id="e13aa-143">Connecting to an emulator</span></span>

<span data-ttu-id="e13aa-144">您也可以透過模擬器使用 Device Portal。</span><span class="sxs-lookup"><span data-stu-id="e13aa-144">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="e13aa-145">若要連線到裝置入口網站，請使用[工具列](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-145">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="e13aa-146">按一下這個圖示：![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="e13aa-146">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="e13aa-147">建立使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="e13aa-147">Creating a Username and Password</span></span>

<span data-ttu-id="e13aa-148">![設定 Windows 裝置入口網站的存取權](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-148">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-149">設定 Windows 裝置入口網站的存取權 </span><span class="sxs-lookup"><span data-stu-id="e13aa-149">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="e13aa-150">首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="e13aa-150">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="e13aa-151">在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e13aa-151">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="e13aa-152">[設定存取] 頁面將會開啟。</span><span class="sxs-lookup"><span data-stu-id="e13aa-152">The Set up access page opens.</span></span>
2. <span data-ttu-id="e13aa-153">按一下或點選 [要求 PIN]  ，並查看 HoloLens 顯示畫面，以取得所產生的 PIN。</span><span class="sxs-lookup"><span data-stu-id="e13aa-153">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="e13aa-154">輸入 [您裝置上顯示的 PIN]  文字方塊中的 PIN。</span><span class="sxs-lookup"><span data-stu-id="e13aa-154">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="e13aa-155">輸入您會用來連線到 Device Portal 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e13aa-155">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="e13aa-156">它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。</span><span class="sxs-lookup"><span data-stu-id="e13aa-156">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="e13aa-157">輸入密碼並確認它。</span><span class="sxs-lookup"><span data-stu-id="e13aa-157">Enter a password and confirm it.</span></span> <span data-ttu-id="e13aa-158">密碼長度必須至少為七個字元。</span><span class="sxs-lookup"><span data-stu-id="e13aa-158">The password must be at least seven characters in length.</span></span> <span data-ttu-id="e13aa-159">它並不需要是 MSA 或網域密碼。</span><span class="sxs-lookup"><span data-stu-id="e13aa-159">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="e13aa-160">按一下 [配對]  ，在 HoloLens 上連線到 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="e13aa-160">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="e13aa-161">如果您想在任何時候變更此使用者名稱或密碼，可以造訪裝置安全性頁面來重複此程序，方法是瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm。</span><span class="sxs-lookup"><span data-stu-id="e13aa-161">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="e13aa-162">安全性憑證</span><span class="sxs-lookup"><span data-stu-id="e13aa-162">Security certificate</span></span>

<span data-ttu-id="e13aa-163">如果您在瀏覽器中看見「憑證錯誤」，可透過與裝置建立信任關係來加以修正。</span><span class="sxs-lookup"><span data-stu-id="e13aa-163">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="e13aa-164">每個 HoloLens 都會為其 SSL 連線產生唯一的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="e13aa-164">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="e13aa-165">根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。</span><span class="sxs-lookup"><span data-stu-id="e13aa-165">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="e13aa-166">藉由從您的 HoloLens 下載此憑證 (透過 USB 或您信任的 Wi-Fi 網路)，並在電腦上信任它，您便能安全地連線到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="e13aa-166">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="e13aa-167">**請確保您是在安全的網路上 (USB 或您信任的 Wi-Fi 網路)。**</span><span class="sxs-lookup"><span data-stu-id="e13aa-167">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="e13aa-168">從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。</span><span class="sxs-lookup"><span data-stu-id="e13aa-168">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="e13aa-169">瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="e13aa-169">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="e13aa-170">開啟 [系統] > [喜好設定] 的節點。</span><span class="sxs-lookup"><span data-stu-id="e13aa-170">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="e13aa-171">向下捲動至 [裝置安全性]，按一下 [下載此裝置的憑證] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e13aa-171">Scroll down to Device Security, click the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="e13aa-172">安裝您電腦上「信任的根憑證授權」存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="e13aa-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="e13aa-173">從 [Windows] 功能表中，輸入：管理電腦憑證並啟動 applet。</span><span class="sxs-lookup"><span data-stu-id="e13aa-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="e13aa-174">展開 [信任的根憑證授權]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="e13aa-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="e13aa-175">按一下 [憑證]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="e13aa-175">Click the **Certificates** folder.</span></span>
   * <span data-ttu-id="e13aa-176">從 [動作] 功能表中，選取：[所有工作] > [匯入]...</span><span class="sxs-lookup"><span data-stu-id="e13aa-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="e13aa-177">使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="e13aa-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="e13aa-178">重新啟動瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e13aa-178">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="e13aa-179">僅在裝置刷新時，才會信任此裝置的憑證，且使用者才必須再次執行此程序。</span><span class="sxs-lookup"><span data-stu-id="e13aa-179">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>


## <a name="device-portal-pages"></a><span data-ttu-id="e13aa-180">Device Portal 頁面</span><span class="sxs-lookup"><span data-stu-id="e13aa-180">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="e13aa-181">首頁</span><span class="sxs-lookup"><span data-stu-id="e13aa-181">Home</span></span>

<span data-ttu-id="e13aa-182">![Microsoft HoloLens 上的 Windows 裝置入口網站首頁](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-182">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-183">*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*</span><span class="sxs-lookup"><span data-stu-id="e13aa-183">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-184">您的 Device Portal 工作階段從首頁開始。</span><span class="sxs-lookup"><span data-stu-id="e13aa-184">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="e13aa-185">從首頁左側的瀏覽列中存取其他頁面。</span><span class="sxs-lookup"><span data-stu-id="e13aa-185">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="e13aa-186">頁面頂端的工具列能讓您存取常用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="e13aa-186">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="e13aa-187">**線上**：指出裝置是否已連線到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="e13aa-187">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="e13aa-188">**關機**：關閉裝置。</span><span class="sxs-lookup"><span data-stu-id="e13aa-188">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="e13aa-189">**重新啟動**：關閉裝置電源並重新開啟。</span><span class="sxs-lookup"><span data-stu-id="e13aa-189">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="e13aa-190">**安全性**：開啟 [裝置安全性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e13aa-190">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="e13aa-191">**冷卻**：指出裝置的溫度。</span><span class="sxs-lookup"><span data-stu-id="e13aa-191">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="e13aa-192">**A/C**：指出裝置是否已插上電源並且正在充電。</span><span class="sxs-lookup"><span data-stu-id="e13aa-192">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="e13aa-193">**說明**：開啟 REST 介面文件頁面。</span><span class="sxs-lookup"><span data-stu-id="e13aa-193">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="e13aa-194">首頁將顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e13aa-194">The home page shows the following info:</span></span>
* <span data-ttu-id="e13aa-195">**裝置狀態：** 監視裝置的健康狀況並報告嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-195">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="e13aa-196">**Windows 資訊：** 顯示 HoloLens 的名稱，以及目前安裝的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="e13aa-196">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="e13aa-197">[喜好設定]  區段包含下列設定：</span><span class="sxs-lookup"><span data-stu-id="e13aa-197">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="e13aa-198">**IPD**：設定瞳孔間距 (IPD)，這是使用者雙眼注視前方時，兩個瞳孔中心點之間的距離 (以公釐為單位)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-198">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="e13aa-199">此設定會立即生效。</span><span class="sxs-lookup"><span data-stu-id="e13aa-199">The setting takes effect immediately.</span></span> <span data-ttu-id="e13aa-200">預設值會在您設定裝置時自動計算。</span><span class="sxs-lookup"><span data-stu-id="e13aa-200">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="e13aa-201">**裝置名稱**：為 HoloLens 指派名稱。</span><span class="sxs-lookup"><span data-stu-id="e13aa-201">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="e13aa-202">在變更此值之後，必須重新啟動裝置才能生效。</span><span class="sxs-lookup"><span data-stu-id="e13aa-202">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="e13aa-203">按一下 [儲存]  之後，將會有對話方塊詢問您是否要立即重新啟動裝置，或稍後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e13aa-203">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="e13aa-204">**睡眠設定**：設定裝置在接上電源及使用電池的情況下，在進入睡眠之前所需等待的時間長度。</span><span class="sxs-lookup"><span data-stu-id="e13aa-204">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="e13aa-205">3D 檢視</span><span class="sxs-lookup"><span data-stu-id="e13aa-205">3D View</span></span>

<span data-ttu-id="e13aa-206">![Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-206">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-207">*Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-207">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-208">使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-208">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="e13aa-209">使用滑鼠來瀏覽檢視：</span><span class="sxs-lookup"><span data-stu-id="e13aa-209">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="e13aa-210">旋轉：按下滑鼠左鍵 + 移動滑鼠；</span><span class="sxs-lookup"><span data-stu-id="e13aa-210">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="e13aa-211">平移：按下滑鼠右鍵 + 移動滑鼠；</span><span class="sxs-lookup"><span data-stu-id="e13aa-211">Pan: right click + mouse;</span></span>
* <span data-ttu-id="e13aa-212">縮放：滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="e13aa-212">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="e13aa-213">**追蹤選項**</span><span class="sxs-lookup"><span data-stu-id="e13aa-213">**Tracking options**</span></span>
   * <span data-ttu-id="e13aa-214">選取 [強制視覺追蹤]  來開啟持續性視覺追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-214">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="e13aa-215">**暫停**將會停止視覺追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-215">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="e13aa-216">**檢視選項**：設定 3D 視圖上的選項：</span><span class="sxs-lookup"><span data-stu-id="e13aa-216">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="e13aa-217">**追蹤**：指出視覺追蹤是否為作用中。</span><span class="sxs-lookup"><span data-stu-id="e13aa-217">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="e13aa-218">**顯示樓面**：顯示棋盤式的樓面規劃。</span><span class="sxs-lookup"><span data-stu-id="e13aa-218">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="e13aa-219">**顯示範圍**：顯示檢視範圍。</span><span class="sxs-lookup"><span data-stu-id="e13aa-219">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="e13aa-220">**顯示穩定平面**：顯示 HoloLens 用來穩定動作的平面。</span><span class="sxs-lookup"><span data-stu-id="e13aa-220">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="e13aa-221">**顯示網格**：顯示代表您周遭環境的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="e13aa-221">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="e13aa-222">**顯示空間錨點**：顯示作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="e13aa-222">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="e13aa-223">您必須按一下 [更新] 按鈕，才能取得並重新整理錨點。</span><span class="sxs-lookup"><span data-stu-id="e13aa-223">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="e13aa-224">**顯示詳細資料**：隨著下列數據變更，即時顯示雙手位置、頭部旋轉四元數，以及裝置原點向量。</span><span class="sxs-lookup"><span data-stu-id="e13aa-224">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="e13aa-225">**全螢幕按鈕**：以全螢幕模式顯示 3D 檢視。</span><span class="sxs-lookup"><span data-stu-id="e13aa-225">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="e13aa-226">按下 ESC 以離開全螢幕檢視。</span><span class="sxs-lookup"><span data-stu-id="e13aa-226">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="e13aa-227">**表面重建**：按一下或點選 [更新]  以顯示裝置中最新的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="e13aa-227">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="e13aa-228">可能需要花費一些時間 (最多幾秒鐘) 才能完成完整作業。</span><span class="sxs-lookup"><span data-stu-id="e13aa-228">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="e13aa-229">網格並不會在 3D 檢視中自動更新，您必須手動按一下 [更新]  以取得來自裝置的最新網格。</span><span class="sxs-lookup"><span data-stu-id="e13aa-229">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="e13aa-230">按一下 [儲存]  ，將目前的空間對應網格在您的電腦上儲存為 obj 檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-230">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="e13aa-231">**空間錨點**：按一下 [更新] 以顯示或更新作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="e13aa-231">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="e13aa-232">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="e13aa-232">Mixed Reality Capture</span></span>

<span data-ttu-id="e13aa-233">![Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-233">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-234">*Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-234">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-235">使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-235">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="e13aa-236">**設定**：藉由檢查下列設定來控制所擷取的媒體串流：</span><span class="sxs-lookup"><span data-stu-id="e13aa-236">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="e13aa-237">**全像投影**：在影片串流中擷取全像投影內容。</span><span class="sxs-lookup"><span data-stu-id="e13aa-237">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="e13aa-238">全像投影是以單聲道進行轉譯，而非立體聲。</span><span class="sxs-lookup"><span data-stu-id="e13aa-238">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="e13aa-239">**PV 相機**：擷取來自相片/攝影機的影片串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-239">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="e13aa-240">**麥克風音訊**：擷取來自麥克風陣列的音訊。</span><span class="sxs-lookup"><span data-stu-id="e13aa-240">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="e13aa-241">**App 音訊**：擷取來自目前執行中 App 的音訊。</span><span class="sxs-lookup"><span data-stu-id="e13aa-241">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="e13aa-242">**從相機呈現**：如果[受執行中應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (僅限 HoloLens 2)，則將要從相片/攝影機角度進行的擷取對齊。</span><span class="sxs-lookup"><span data-stu-id="e13aa-242">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="e13aa-243">**即時預覽品質**：選取即時預覽的螢幕解析度、畫面播放速率，以及串流速率。</span><span class="sxs-lookup"><span data-stu-id="e13aa-243">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="e13aa-244">按一下或點選 [即時預覽]  按鈕以顯示擷取串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-244">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="e13aa-245">**停止即時預覽**將會停止擷取串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-245">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="e13aa-246">按一下或點選 [錄製]  ，開始使用指定的設定來錄製混合實境串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-246">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="e13aa-247">**停止錄製**將會中止並儲存錄製內容。</span><span class="sxs-lookup"><span data-stu-id="e13aa-247">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="e13aa-248">按一下或點選 [拍攝相片]  ，從擷取串流中拍攝靜止影像。</span><span class="sxs-lookup"><span data-stu-id="e13aa-248">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="e13aa-249">**影片與相片**：顯示在裝置上所拍攝影片和相片擷取的清單。</span><span class="sxs-lookup"><span data-stu-id="e13aa-249">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="e13aa-250">[同步 MRC 有以下限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="e13aa-250">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="e13aa-251">如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機，將會停止影片錄製。</span><span class="sxs-lookup"><span data-stu-id="e13aa-251">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="e13aa-252">如果應用程式透過 SharedReadOnly 模式存取相片/攝影機，則 HoloLens 2 不會停止錄製影片。</span><span class="sxs-lookup"><span data-stu-id="e13aa-252">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="e13aa-253">如果應用程式主動使用相片/攝影機，Windows 裝置入口網站就能夠拍攝相片或錄製影片。</span><span class="sxs-lookup"><span data-stu-id="e13aa-253">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="e13aa-254">即時串流：</span><span class="sxs-lookup"><span data-stu-id="e13aa-254">Live streaming:</span></span>
>   * <span data-ttu-id="e13aa-255">HoloLens (第 1 代) 可避免應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="e13aa-255">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="e13aa-256">如果應用程式主動使用相片/攝影機，HoloLens (第 1 代) 將無法即時串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-256">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="e13aa-257">當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時，HoloLens 2 會自動停止即時串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-257">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="e13aa-258">當應用程式主動使用 PV 相機時，HoloLens 2 可以啟動即時串流。</span><span class="sxs-lookup"><span data-stu-id="e13aa-258">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="e13aa-259">效能追蹤</span><span class="sxs-lookup"><span data-stu-id="e13aa-259">Performance Tracing</span></span>

<span data-ttu-id="e13aa-260">![Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-260">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-261">*Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-261">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-262">從您的 HoloLens 擷取 [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) 追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-262">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="e13aa-263">**可用的設定檔**：從下拉式清單選取 WPR 設定檔，然後按一下或點選 [開始]  以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-263">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="e13aa-264">**自訂設定檔**：按一下或點選 [瀏覽]  ，以從您的電腦選擇 WPR 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e13aa-264">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="e13aa-265">按一下或點選 [上傳並開始]  以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-265">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="e13aa-266">若要停止追蹤，請按一下 [停止] 連結。</span><span class="sxs-lookup"><span data-stu-id="e13aa-266">To stop the trace, click the stop link.</span></span> <span data-ttu-id="e13aa-267">留在此頁面上，直到追蹤檔案下載完成。</span><span class="sxs-lookup"><span data-stu-id="e13aa-267">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="e13aa-268">擷取的 ETL 檔案可以在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中開啟以進行分析。</span><span class="sxs-lookup"><span data-stu-id="e13aa-268">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="e13aa-269">處理程序</span><span class="sxs-lookup"><span data-stu-id="e13aa-269">Processes</span></span>

<span data-ttu-id="e13aa-270">![Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-270">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-271">*Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-271">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-272">顯示有關目前正在執行之處理程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e13aa-272">Shows details about currently running processes.</span></span> <span data-ttu-id="e13aa-273">這包括 App 與系統處理程序。</span><span class="sxs-lookup"><span data-stu-id="e13aa-273">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="e13aa-274">系統效能</span><span class="sxs-lookup"><span data-stu-id="e13aa-274">System Performance</span></span>

<span data-ttu-id="e13aa-275">![Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-275">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-276">*Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-276">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-277">顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。</span><span class="sxs-lookup"><span data-stu-id="e13aa-277">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="e13aa-278">下列為可用的衡量標準：</span><span class="sxs-lookup"><span data-stu-id="e13aa-278">These are the available metrics:</span></span>
* <span data-ttu-id="e13aa-279">**SoC 電源**：系統單晶片電源瞬間使用率 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="e13aa-279">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e13aa-280">**系統電源**：系統電源瞬間使用率 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="e13aa-280">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e13aa-281">**畫面播放速率**：每秒畫面格數、每秒遺失的 VBlanks 數，以及連續遺失的 VBlanks 數</span><span class="sxs-lookup"><span data-stu-id="e13aa-281">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="e13aa-282">**GPU**：GPU 引擎使用率、可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="e13aa-282">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="e13aa-283">**CPU**︰可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="e13aa-283">**CPU**: percent of total available</span></span>
* <span data-ttu-id="e13aa-284">**I/O**：讀取與寫入</span><span class="sxs-lookup"><span data-stu-id="e13aa-284">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="e13aa-285">**網路**：已接收與已傳送</span><span class="sxs-lookup"><span data-stu-id="e13aa-285">**Network**: Received and sent</span></span>
* <span data-ttu-id="e13aa-286">**記憶體**：總計、使用中、已認可的、分頁與非分頁</span><span class="sxs-lookup"><span data-stu-id="e13aa-286">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="e13aa-287">[App]</span><span class="sxs-lookup"><span data-stu-id="e13aa-287">Apps</span></span>

<span data-ttu-id="e13aa-288">![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-288">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-289">*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-289">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-290">管理安裝在 HoloLens 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-290">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="e13aa-291">**已安裝的應用程式**：移除並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-291">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="e13aa-292">**執行中應用程式**：列出目前執行中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-292">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="e13aa-293">**安裝應用程式**：從電腦/網路上的資料夾，選取安裝的應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="e13aa-293">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="e13aa-294">**相依性**：新增所要安裝應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="e13aa-294">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="e13aa-295">**部署**：將選取的應用程式 + 相依性部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e13aa-295">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="e13aa-296">應用程式損毀傾印頁面</span><span class="sxs-lookup"><span data-stu-id="e13aa-296">App Crash Dumps</span></span>

<span data-ttu-id="e13aa-297">![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-297">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-298">*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-298">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-299">此頁面可讓您收集側載 App 的損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="e13aa-299">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="e13aa-300">請針對您想要收集損毀傾印的應用程式，選取其 [啟用的損毀傾印]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e13aa-300">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="e13aa-301">返回此頁面以收集損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="e13aa-301">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="e13aa-302">傾印檔案可以在 [Visual Studio 中開啟以進行偵錯](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-302">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="e13aa-303">檔案總管</span><span class="sxs-lookup"><span data-stu-id="e13aa-303">File Explorer</span></span>

<span data-ttu-id="e13aa-304">![Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-304">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-305">*Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-305">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-306">使用檔案總管來瀏覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-306">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="e13aa-307">您可以針對從 Visual Studio 或裝置入口網站部署的應用程式，使用 [文件] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-307">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="e13aa-308">Kiosk 模式</span><span class="sxs-lookup"><span data-stu-id="e13aa-308">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="e13aa-309">Kiosk 模式僅適用於 [Microsoft HoloLens Commercial Suite](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-309">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="e13aa-310">如需透過 Windows 裝置入口網站啟用 Kiosk 模式的最新指示，請參閱 Windows IT Pro 中心的[以 Kiosk 模式設定 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 文章。</span><span class="sxs-lookup"><span data-stu-id="e13aa-310">Check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="e13aa-311">記錄</span><span class="sxs-lookup"><span data-stu-id="e13aa-311">Logging</span></span>

<span data-ttu-id="e13aa-312">![Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-312">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-313">*Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-313">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-314">管理 HoloLens 上的即時 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-314">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="e13aa-315">選取 [隱藏提供者]  ，以只顯示 [事件]  清單。</span><span class="sxs-lookup"><span data-stu-id="e13aa-315">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="e13aa-316">**已註冊的提供者**：選取 ETW 提供者與追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="e13aa-316">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="e13aa-317">追蹤等級是下列其中一個值 ︰</span><span class="sxs-lookup"><span data-stu-id="e13aa-317">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="e13aa-318">異常結束或終止</span><span class="sxs-lookup"><span data-stu-id="e13aa-318">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="e13aa-319">嚴重錯誤</span><span class="sxs-lookup"><span data-stu-id="e13aa-319">Severe errors</span></span>
   3. <span data-ttu-id="e13aa-320">警告</span><span class="sxs-lookup"><span data-stu-id="e13aa-320">Warnings</span></span>
   4. <span data-ttu-id="e13aa-321">非錯誤警告</span><span class="sxs-lookup"><span data-stu-id="e13aa-321">Non-error warnings</span></span>

<span data-ttu-id="e13aa-322">按一下或點選 [啟用]  以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-322">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="e13aa-323">提供者已新增到 [啟用的提供者]  下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="e13aa-323">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="e13aa-324">**自訂提供者**：選取自訂 ETW 提供者與追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="e13aa-324">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="e13aa-325">依 GUID 識別提供者。</span><span class="sxs-lookup"><span data-stu-id="e13aa-325">Identify the provider by its GUID.</span></span> <span data-ttu-id="e13aa-326">不要在 GUID 中包含括號。</span><span class="sxs-lookup"><span data-stu-id="e13aa-326">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="e13aa-327">**啟用的提供者**：列出已啟用的提供者。</span><span class="sxs-lookup"><span data-stu-id="e13aa-327">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="e13aa-328">從下拉式清單選取提供者，然後按一下或點選 [停用]  以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-328">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="e13aa-329">按一下或點選 [全部停止]  以暫停所有追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13aa-329">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="e13aa-330">**提供者歷程記錄**：顯示目前工作階段期間已啟用的 ETW 提供者。</span><span class="sxs-lookup"><span data-stu-id="e13aa-330">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="e13aa-331">按一下或點選 [啟用]  以啟用已停用的提供者。</span><span class="sxs-lookup"><span data-stu-id="e13aa-331">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="e13aa-332">按一下或點選 [清除]  以清除歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="e13aa-332">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="e13aa-333">**事件**：以表格格式列出所選提供者的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e13aa-333">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="e13aa-334">此表格會即時更新。</span><span class="sxs-lookup"><span data-stu-id="e13aa-334">This table is updated in real time.</span></span> <span data-ttu-id="e13aa-335">在表格下方，按一下 [清除]  按鈕，以刪除表格中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e13aa-335">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="e13aa-336">這不會停用任何提供者。</span><span class="sxs-lookup"><span data-stu-id="e13aa-336">This does not disable any providers.</span></span> <span data-ttu-id="e13aa-337">您可以按一下 [儲存到檔案]  ，在本機將目前收集的 ETW 事件匯出到 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-337">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="e13aa-338">**篩選**：可讓您篩選由識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e13aa-338">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="e13aa-339">您可以將數個準則結合在一起：</span><span class="sxs-lookup"><span data-stu-id="e13aa-339">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="e13aa-340">針對套用至相同屬性的準則，會顯示可滿足任一準則的事件。</span><span class="sxs-lookup"><span data-stu-id="e13aa-340">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="e13aa-341">針對套用至不同屬性的準則，事件必須滿足所有準則</span><span class="sxs-lookup"><span data-stu-id="e13aa-341">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="e13aa-342">例如，您可以指定準則 *(工作名稱包含 'Foo' 或 'Bar') AND (文字包含 'error' 或 'warning')*</span><span class="sxs-lookup"><span data-stu-id="e13aa-342">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="e13aa-343">模擬</span><span class="sxs-lookup"><span data-stu-id="e13aa-343">Simulation</span></span>

<span data-ttu-id="e13aa-344">![Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-344">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-345">*Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-345">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-346">允許您記錄並播放輸入資料以進行測試。</span><span class="sxs-lookup"><span data-stu-id="e13aa-346">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="e13aa-347">**擷取房間**：用來下載模擬的房間檔案，其中包含針對使用者周遭環境的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="e13aa-347">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="e13aa-348">為房間命名，然後按一下 [擷取]  ，在您的電腦上將資料儲存為 .xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-348">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e13aa-349">此房間檔案可以載入 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="e13aa-349">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="e13aa-350">**錄製**：檢查要錄製的串流、為錄製命名，然後按一下或點選 [錄製]  開始錄製。</span><span class="sxs-lookup"><span data-stu-id="e13aa-350">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="e13aa-351">使用您的 HoloLens 執行動作，然後按一下 [停止]  ，在您的電腦上將資料儲存為 .xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="e13aa-351">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e13aa-352">此檔案可以載入 HoloLens 模擬器或裝置。</span><span class="sxs-lookup"><span data-stu-id="e13aa-352">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="e13aa-353">**播放**：按一下或點選 [上傳錄製]  ，從電腦中選取 xef 檔案，並將資料傳送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e13aa-353">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="e13aa-354">**控制模式**：從下拉式清單中選取 [預設]  或 [模擬]  ，然後按一下或點選 [設定]  按鈕來選取 HoloLens 上的模式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-354">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="e13aa-355">選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。</span><span class="sxs-lookup"><span data-stu-id="e13aa-355">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="e13aa-356">如果您切換到 [模擬]，您的 HoloLens 將不會對真實使用者做出回應，直到您切換回 [預設] 為止。</span><span class="sxs-lookup"><span data-stu-id="e13aa-356">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="e13aa-357">網路功能</span><span class="sxs-lookup"><span data-stu-id="e13aa-357">Networking</span></span>

<span data-ttu-id="e13aa-358">![Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-358">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-359">*Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-359">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-360">管理 HoloLens 上的 Wi-Fi 連線。</span><span class="sxs-lookup"><span data-stu-id="e13aa-360">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="e13aa-361">**WiFi 介面卡**：使用下拉式清單控制項選取 Wi-Fi 介面卡和設定檔。</span><span class="sxs-lookup"><span data-stu-id="e13aa-361">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="e13aa-362">按一下或點擊 [連線]  以使用選取的介面卡。</span><span class="sxs-lookup"><span data-stu-id="e13aa-362">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="e13aa-363">**可用網路**：列出 HoloLens 可以連線的 Wi-Fi 網路。</span><span class="sxs-lookup"><span data-stu-id="e13aa-363">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="e13aa-364">按一下或點選 [重新整理]  以更新清單。</span><span class="sxs-lookup"><span data-stu-id="e13aa-364">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="e13aa-365">**IP 設定**：顯示網路連線的 IP 位址和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e13aa-365">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="e13aa-366">虛擬輸入</span><span class="sxs-lookup"><span data-stu-id="e13aa-366">Virtual Input</span></span>

<span data-ttu-id="e13aa-367">![Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13aa-367">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="e13aa-368">*Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面*</span><span class="sxs-lookup"><span data-stu-id="e13aa-368">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e13aa-369">從遠端電腦傳送鍵盤輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e13aa-369">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="e13aa-370">按一下或點選 [虛擬鍵盤]  下方的區域，來啟用傳送按鍵輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e13aa-370">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="e13aa-371">在 [輸入文字]  文字方塊中輸入，然後按一下或點選 [傳送]  ，將按鍵輸入傳送到使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-371">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="e13aa-372">裝置入口網站 REST API</span><span class="sxs-lookup"><span data-stu-id="e13aa-372">Device Portal REST API's</span></span>

<span data-ttu-id="e13aa-373">裝置入口網站中所有的項目都是以 [REST API](device-portal-api-reference.md) (可選擇性地讓您用來存取資料，並以程式設計方式控制裝置) 為基礎所建置。</span><span class="sxs-lookup"><span data-stu-id="e13aa-373">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
