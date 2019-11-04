---
title: 版本資訊-2016 年8月
description: Windows 10 年度版本的 HoloLens 版本資訊（2016年）
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，版本資訊，os，平臺，功能，商業套件
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438099"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="fc234-104">版本資訊-2016 年8月</span><span class="sxs-lookup"><span data-stu-id="fc234-104">Release notes - August 2016</span></span>

<span data-ttu-id="fc234-105">HoloLens 團隊正在接聽 Windows 測試人員計畫中的開發人員意見反應，以排定工作的優先順序。</span><span class="sxs-lookup"><span data-stu-id="fc234-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="fc234-106">請透過 @HoloLens，繼續提供意見反應中樞、[開發人員論壇](https://forums.hololens.com)和[Twitter](https://twitter.com/hololens)的[意見反應給我們](give-us-feedback.md)。</span><span class="sxs-lookup"><span data-stu-id="fc234-106">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="fc234-107">隨著 Windows 10 的年度更新，HoloLens 團隊很高興能為全像攝影體驗提供進一步的改進。</span><span class="sxs-lookup"><span data-stu-id="fc234-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="fc234-108">在此更新中，我們著重于主要的修正程式、改良功能，以及企業所要求並可在 Microsoft HoloLens 商業套件中取得的功能。</span><span class="sxs-lookup"><span data-stu-id="fc234-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="fc234-109">**最新版本：** Windows 全像2016年8月更新（**10.0.14393.0**，windows 10 年度發行版本）</span><span class="sxs-lookup"><span data-stu-id="fc234-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="fc234-110">若要[更新為目前的版本](updating-hololens.md)，請開啟 [*設定*] 應用程式，移至 [*更新 & 安全性*]，然後選取 [*檢查更新*] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fc234-110">To [update to the current release](updating-hololens.md), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="fc234-111">新功能</span><span class="sxs-lookup"><span data-stu-id="fc234-111">New features</span></span>

<span data-ttu-id="fc234-112">**附加至進程的調試**程式HoloLens 現在支援附加至進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="fc234-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="fc234-113">您可以使用 Visual Studio 2015 Update 3 來連線至 HoloLens 上執行中的應用程式，並[開始對其進行調試](using-visual-studio.md#debugging-an-installed-or-running-app)。</span><span class="sxs-lookup"><span data-stu-id="fc234-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](using-visual-studio.md#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="fc234-114">這種方式不需要從 Visual Studio 專案進行部署。</span><span class="sxs-lookup"><span data-stu-id="fc234-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="fc234-115">**已更新 HoloLens 模擬器**我們也已發行 HoloLens 模擬器的更新版本。</span><span class="sxs-lookup"><span data-stu-id="fc234-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="fc234-116">**遊戲台支援**您現在可以將藍牙遊戲台與 HoloLens 配對！</span><span class="sxs-lookup"><span data-stu-id="fc234-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="fc234-117">新發行的 Xbox 無線控制器具有藍牙功能，可用來播放您最愛的遊戲和應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc234-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="fc234-118">您必須先套用[控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，才能將 Xbox 無線控制器與 HoloLens 連接。</span><span class="sxs-lookup"><span data-stu-id="fc234-118">A [controller update](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="fc234-119">Xbox 無線控制器支援[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)和[Windows 遊戲。輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)api。</span><span class="sxs-lookup"><span data-stu-id="fc234-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="fc234-120">您可以透過[Windows. 遊戲輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)API 來存取其他的藍牙控制器型號。</span><span class="sxs-lookup"><span data-stu-id="fc234-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="fc234-121">改良功能與修正</span><span class="sxs-lookup"><span data-stu-id="fc234-121">Improvements and fixes</span></span>

<span data-ttu-id="fc234-122">我們會與其余的 Windows 10 年度更新版同步，因此除了 HoloLens 特有的修正程式之外，您也會收到 Windows update 的所有好處，以提高平臺的可靠性和效能。</span><span class="sxs-lookup"><span data-stu-id="fc234-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the HoloLens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="fc234-123">您的意見反應具有高價值，且優先于版本中的修正。</span><span class="sxs-lookup"><span data-stu-id="fc234-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="fc234-124">我們已改善下列體驗：</span><span class="sxs-lookup"><span data-stu-id="fc234-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="fc234-125">登入體驗。</span><span class="sxs-lookup"><span data-stu-id="fc234-125">log in experiences.</span></span>
* <span data-ttu-id="fc234-126">加入工作場所。</span><span class="sxs-lookup"><span data-stu-id="fc234-126">workplace join.</span></span>
* <span data-ttu-id="fc234-127">裝置電源狀態轉換的電源效率。</span><span class="sxs-lookup"><span data-stu-id="fc234-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="fc234-128">混合現實的穩定性。</span><span class="sxs-lookup"><span data-stu-id="fc234-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="fc234-129">藍牙連線能力的可靠性</span><span class="sxs-lookup"><span data-stu-id="fc234-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="fc234-130">多個應用程式案例中的全息影像持續性。</span><span class="sxs-lookup"><span data-stu-id="fc234-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="fc234-131">我們已修正下列問題：</span><span class="sxs-lookup"><span data-stu-id="fc234-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="fc234-132">Visual Studio 分析工具和圖形偵錯工具無法連接。</span><span class="sxs-lookup"><span data-stu-id="fc234-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="fc234-133">相片 & 檔不會顯示在裝置入口網站的檔案瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="fc234-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="fc234-134">當游標放在調整模式的上方時，應用程式行就會閃爍。</span><span class="sxs-lookup"><span data-stu-id="fc234-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="fc234-135">當處於調整模式時，眼睛點游標將會變得更慢。</span><span class="sxs-lookup"><span data-stu-id="fc234-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="fc234-136">「嗨，Cortana play 音樂」並不會啟動 Groove。</span><span class="sxs-lookup"><span data-stu-id="fc234-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="fc234-137">在上一次更新之後，表示 "Go Home" 不會正確顯示 pin 面板。</span><span class="sxs-lookup"><span data-stu-id="fc234-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="fc234-138">Microsoft HoloLens 商業套件簡介</span><span class="sxs-lookup"><span data-stu-id="fc234-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="fc234-139">Microsoft HoloLens 商業套件已準備好進行企業部署。</span><span class="sxs-lookup"><span data-stu-id="fc234-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="fc234-140">我們已從我們的早期企業合作夥伴新增數個高度要求的[商業功能](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="fc234-140">We've added several highly requested [commercial features](commercial-features.md) from our early business partners.</span></span>

<span data-ttu-id="fc234-141">請洽詢您當地的 Microsoft 帳戶經理，以購買 Microsoft HoloLens 商用套件。</span><span class="sxs-lookup"><span data-stu-id="fc234-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="fc234-142">主要的商業功能</span><span class="sxs-lookup"><span data-stu-id="fc234-142">Key Commercial Features</span></span> 

* <span data-ttu-id="fc234-143">**Kiosk 模式。**</span><span class="sxs-lookup"><span data-stu-id="fc234-143">**Kiosk mode.**</span></span> <span data-ttu-id="fc234-144">使用 HoloLens kiosk 模式時，您可以限制要執行哪些應用程式，以啟用示範或展示體驗。</span><span class="sxs-lookup"><span data-stu-id="fc234-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="fc234-145">以 kiosk 模式 ![，HoloLens 會直接啟動您選擇的應用程式。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="fc234-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="fc234-146">**適用于 HoloLens 的行動裝置管理（MDM）。**</span><span class="sxs-lookup"><span data-stu-id="fc234-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="fc234-147">您的 IT 部門可以使用 Microsoft Intune 之類的解決方案同時管理多個 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="fc234-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="fc234-148">您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fc234-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="fc234-149">HoloLens 上的 ![行動裝置管理可提供跨多個裝置的企業級裝置管理。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="fc234-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="fc234-150">**商務用 Windows Update。**</span><span class="sxs-lookup"><span data-stu-id="fc234-150">**Windows Update for Business.**</span></span> <span data-ttu-id="fc234-151">對裝置進行受控制的作業系統更新，並支援長期維護分支。</span><span class="sxs-lookup"><span data-stu-id="fc234-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="fc234-152">**資料安全性。**</span><span class="sxs-lookup"><span data-stu-id="fc234-152">**Data security.**</span></span> <span data-ttu-id="fc234-153">HoloLens 上已啟用 BitLocker 資料加密，以提供與任何其他 Windows 裝置相同層級的安全性保護。</span><span class="sxs-lookup"><span data-stu-id="fc234-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="fc234-154">**工作存取。**</span><span class="sxs-lookup"><span data-stu-id="fc234-154">**Work access.**</span></span> <span data-ttu-id="fc234-155">您組織中的任何人都可以透過 HoloLens 上的虛擬私人網路，從遠端連線到公司網路。</span><span class="sxs-lookup"><span data-stu-id="fc234-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="fc234-156">HoloLens 也可以存取需要認證的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="fc234-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="fc234-157">**商務用 Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="fc234-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="fc234-158">您的 IT 部門也可以設定企業私人存放區，只包含您的公司應用程式，以符合您特定的 HoloLens 使用量。</span><span class="sxs-lookup"><span data-stu-id="fc234-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="fc234-159">安全地將您的企業軟體散發給所選的企業使用者群組。</span><span class="sxs-lookup"><span data-stu-id="fc234-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="fc234-160">開發版與商業套件</span><span class="sxs-lookup"><span data-stu-id="fc234-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="fc234-161">功能</span><span class="sxs-lookup"><span data-stu-id="fc234-161">Features</span></span></th><th><span data-ttu-id="fc234-162">開發版</span><span class="sxs-lookup"><span data-stu-id="fc234-162">Development Edition</span></span></th><th><span data-ttu-id="fc234-163">商業套件</span><span class="sxs-lookup"><span data-stu-id="fc234-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="fc234-164">裝置加密（Bitlocker）</span><span class="sxs-lookup"><span data-stu-id="fc234-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-165">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-166">虛擬私人網路 (VPN)</span><span class="sxs-lookup"><span data-stu-id="fc234-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-167">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk 模式</a></span><span class="sxs-lookup"><span data-stu-id="fc234-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-169">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="fc234-170">管理與部署</span><span class="sxs-lookup"><span data-stu-id="fc234-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="fc234-171">行動裝置管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="fc234-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="fc234-172">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-173">封鎖取消註冊的能力</span><span class="sxs-lookup"><span data-stu-id="fc234-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-174">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-175">以憑證為基礎的公司 Wi-fi 存取</span><span class="sxs-lookup"><span data-stu-id="fc234-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-176">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-177">Microsoft Store （取用者）</span><span class="sxs-lookup"><span data-stu-id="fc234-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-178">型</span><span class="sxs-lookup"><span data-stu-id="fc234-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-179">透過 MDM 篩選</span><span class="sxs-lookup"><span data-stu-id="fc234-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">商務商店入口網站</a></span><span class="sxs-lookup"><span data-stu-id="fc234-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-181">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="fc234-182">安全性和身分識別</span><span class="sxs-lookup"><span data-stu-id="fc234-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="fc234-183">使用 Azure Active Directory （AAD）登入</span><span class="sxs-lookup"><span data-stu-id="fc234-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-184">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-185">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-186">使用 Microsoft 帳戶（MSA）登入</span><span class="sxs-lookup"><span data-stu-id="fc234-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-187">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-188">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-189">具有 PIN 解除鎖定的下一代認證</span><span class="sxs-lookup"><span data-stu-id="fc234-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-190">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-191">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></span><span class="sxs-lookup"><span data-stu-id="fc234-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-193">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-194">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="fc234-195">服務與支援</span><span class="sxs-lookup"><span data-stu-id="fc234-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="fc234-196">自動的系統更新</span><span class="sxs-lookup"><span data-stu-id="fc234-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-197">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="fc234-198">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">商務用 Windows Update</a></span><span class="sxs-lookup"><span data-stu-id="fc234-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-200">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="fc234-201">長期維護分支</span><span class="sxs-lookup"><span data-stu-id="fc234-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="fc234-202">✔️</span><span class="sxs-lookup"><span data-stu-id="fc234-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="fc234-203">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="fc234-203">Prior release notes</span></span>
* [<span data-ttu-id="fc234-204">版本資訊 - 2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="fc234-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="fc234-205">版本資訊 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="fc234-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="fc234-206">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc234-206">See also</span></span>
* [<span data-ttu-id="fc234-207">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="fc234-207">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="fc234-208">商業功能</span><span class="sxs-lookup"><span data-stu-id="fc234-208">Commercial features</span></span>](commercial-features.md)
* [<span data-ttu-id="fc234-209">安裝工具</span><span class="sxs-lookup"><span data-stu-id="fc234-209">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="fc234-210">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="fc234-210">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
