---
title: 版本資訊-2016 年 8 月
description: HoloLens Windows 10 年度版 (2016 年秋季) 的版本資訊
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 版本資訊、 作業系統、 平台、 功能、 commercial suite，
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596356"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="45aed-104">版本資訊-2016 年 8 月</span><span class="sxs-lookup"><span data-stu-id="45aed-104">Release notes - August 2016</span></span>

<span data-ttu-id="45aed-105">HoloLens 小組歡迎提供意見，從開發人員在 Windows Insider 計劃，來排定工作的優先順序。</span><span class="sxs-lookup"><span data-stu-id="45aed-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="45aed-106">請繼續[提供意見反應](give-us-feedback.md)意見反應中樞，透過[開發人員論壇](https://forums.hololens.com)並[透過 Twitter @HoloLens ](https://twitter.com/hololens)。</span><span class="sxs-lookup"><span data-stu-id="45aed-106">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="45aed-107">為 Windows 10 年度更新版，HoloLens 小組很高興能提供的環節進一步提升至全像攝影版的體驗。</span><span class="sxs-lookup"><span data-stu-id="45aed-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="45aed-108">在此更新中，我們會著重於主要修正、 改進及要求的企業，而且可在 Microsoft HoloLens Commercial Suite 簡介的功能。</span><span class="sxs-lookup"><span data-stu-id="45aed-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="45aed-109">**最新版本：** Windows 全像攝影版的年 8 月 2016年更新 (**10.0.14393.0**，Windows 10 年度版)</span><span class="sxs-lookup"><span data-stu-id="45aed-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="45aed-110">若要[目前的版本更新](updating-hololens.md)，開啟*設定*應用程式，移至*更新與安全性*，然後選取*檢查更新*按鈕。</span><span class="sxs-lookup"><span data-stu-id="45aed-110">To [update to the current release](updating-hololens.md), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="45aed-111">新功能</span><span class="sxs-lookup"><span data-stu-id="45aed-111">New features</span></span>

<span data-ttu-id="45aed-112">**附加至處理序偵錯**HoloLens 現在支援附加-至-處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="45aed-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="45aed-113">您可以使用 Visual Studio 2015 Update 3 連線到 HoloLens 上執行的應用程式和[開始偵錯](using-visual-studio.md#debugging-an-installed-or-running-app)。</span><span class="sxs-lookup"><span data-stu-id="45aed-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](using-visual-studio.md#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="45aed-114">這適用於不需要從 Visual Studio 專案進行部署。</span><span class="sxs-lookup"><span data-stu-id="45aed-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="45aed-115">**更新 HoloLens 模擬器**我們也發行了 HoloLens 模擬器的更新的版本。</span><span class="sxs-lookup"><span data-stu-id="45aed-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="45aed-116">**遊戲台支援**現在可以配對，並使用藍芽舵 HoloLens 與 ！</span><span class="sxs-lookup"><span data-stu-id="45aed-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="45aed-117">新發行的 Xbox 無線控制器 S 藍芽功能的功能，而且可用來播放您最愛的遊戲台啟用遊戲和應用程式。</span><span class="sxs-lookup"><span data-stu-id="45aed-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="45aed-118">A[控制器更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)則必須先在 Xbox 無線控制器 S 交流 HoloLens 套用。</span><span class="sxs-lookup"><span data-stu-id="45aed-118">A [controller update](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="45aed-119">Xbox 無線控制器 S 受到[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)並[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。</span><span class="sxs-lookup"><span data-stu-id="45aed-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="45aed-120">可透過存取其他模型的藍牙控制器[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。</span><span class="sxs-lookup"><span data-stu-id="45aed-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="45aed-121">改進功能與修正</span><span class="sxs-lookup"><span data-stu-id="45aed-121">Improvements and fixes</span></span>

<span data-ttu-id="45aed-122">我們是與其餘的 Windows 10 年度更新版，同步的因此除了 Hololens 特定修正程式，您也收到所有優點從 Windows update，以提高平台的可靠性和效能。</span><span class="sxs-lookup"><span data-stu-id="45aed-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the Hololens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="45aed-123">您的意見反應是高值及針對修正版本中設定優先順序。</span><span class="sxs-lookup"><span data-stu-id="45aed-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="45aed-124">我們已改進下列體驗：</span><span class="sxs-lookup"><span data-stu-id="45aed-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="45aed-125">登入體驗。</span><span class="sxs-lookup"><span data-stu-id="45aed-125">log in experiences.</span></span>
* <span data-ttu-id="45aed-126">加入工作地點。</span><span class="sxs-lookup"><span data-stu-id="45aed-126">workplace join.</span></span>
* <span data-ttu-id="45aed-127">裝置的電源狀態轉換的電源效率。</span><span class="sxs-lookup"><span data-stu-id="45aed-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="45aed-128">使用混合實境擷取的穩定性。</span><span class="sxs-lookup"><span data-stu-id="45aed-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="45aed-129">藍牙連線的可靠性</span><span class="sxs-lookup"><span data-stu-id="45aed-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="45aed-130">在多個應用程式案例的全像持續性。</span><span class="sxs-lookup"><span data-stu-id="45aed-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="45aed-131">我們已修正下列問題：</span><span class="sxs-lookup"><span data-stu-id="45aed-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="45aed-132">Visual Studio 分析工具和圖形偵錯工具無法連線。</span><span class="sxs-lookup"><span data-stu-id="45aed-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="45aed-133">相片和文件不會出現在檔案總管 中，在裝置入口網站中。</span><span class="sxs-lookup"><span data-stu-id="45aed-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="45aed-134">當游標置於上方調整模式中，可以閃爍應用程式列中。</span><span class="sxs-lookup"><span data-stu-id="45aed-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="45aed-135">在 [調整] 模式中，眼睛視線點游標會變更為 4 箭號游標一段時間更慢。</span><span class="sxs-lookup"><span data-stu-id="45aed-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="45aed-136">「 嘿 Cortana 播放音樂 」 不會啟動 Groove。</span><span class="sxs-lookup"><span data-stu-id="45aed-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="45aed-137">上一個更新之後，"Home 移"說不會顯示 pin 面板正確。</span><span class="sxs-lookup"><span data-stu-id="45aed-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="45aed-138">簡介 Microsoft HoloLens 商業套件</span><span class="sxs-lookup"><span data-stu-id="45aed-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="45aed-139">Microsoft HoloLens Commercial Suite，可供企業部署。</span><span class="sxs-lookup"><span data-stu-id="45aed-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="45aed-140">我們已新增數個高要求[商業功能](commercial-features.md)從我們早期的商業夥伴。</span><span class="sxs-lookup"><span data-stu-id="45aed-140">We've added several highly requested [commercial features](commercial-features.md) from our early business partners.</span></span>

<span data-ttu-id="45aed-141">請連絡當地的 Microsoft 客戶經理，購買 Microsoft HoloLens Commercial Suite。</span><span class="sxs-lookup"><span data-stu-id="45aed-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="45aed-142">重要的商業功能</span><span class="sxs-lookup"><span data-stu-id="45aed-142">Key Commercial Features</span></span> 

* <span data-ttu-id="45aed-143">**Kiosk 模式。**</span><span class="sxs-lookup"><span data-stu-id="45aed-143">**Kiosk mode.**</span></span> <span data-ttu-id="45aed-144">HoloLens kiosk 模式中，您可以限制哪些應用程式來執行以啟用示範或展示的體驗。</span><span class="sxs-lookup"><span data-stu-id="45aed-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="45aed-145">![使用 kiosk 模式時，直接在您選擇的應用程式會啟動 HoloLens。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="45aed-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="45aed-146">**HoloLens 的行動裝置管理 (MDM)。**</span><span class="sxs-lookup"><span data-stu-id="45aed-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="45aed-147">您的 IT 部門可以管理多個的 HoloLens 裝置同時使用 Microsoft Intune 等的解決方案。</span><span class="sxs-lookup"><span data-stu-id="45aed-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="45aed-148">您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="45aed-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="45aed-149">![HoloLens 上的行動裝置管理提供企業級裝置管理跨多個裝置。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="45aed-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="45aed-150">**Windows Update for Business。**</span><span class="sxs-lookup"><span data-stu-id="45aed-150">**Windows Update for Business.**</span></span> <span data-ttu-id="45aed-151">控制裝置和長期維護分支的支援的作業系統更新。</span><span class="sxs-lookup"><span data-stu-id="45aed-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="45aed-152">**資料安全性。**</span><span class="sxs-lookup"><span data-stu-id="45aed-152">**Data security.**</span></span> <span data-ttu-id="45aed-153">HoloLens 上已啟用 BitLocker 資料加密，以提供相同等級的任何其他 Windows 裝置的安全性保護。</span><span class="sxs-lookup"><span data-stu-id="45aed-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="45aed-154">**公司存取。**</span><span class="sxs-lookup"><span data-stu-id="45aed-154">**Work access.**</span></span> <span data-ttu-id="45aed-155">您的組織中的任何人可以遠端連線到公司網路時透過 HoloLens 上的虛擬私人網路。</span><span class="sxs-lookup"><span data-stu-id="45aed-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="45aed-156">HoloLens 也可以存取需要認證的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="45aed-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="45aed-157">**Microsoft Store for Business。**</span><span class="sxs-lookup"><span data-stu-id="45aed-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="45aed-158">您的 IT 部門也可以設定企業的私用存放區，其中包含只供特定的 HoloLens 使用貴公司的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45aed-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="45aed-159">安全地散發您的企業軟體，為選取的企業使用者的群組。</span><span class="sxs-lookup"><span data-stu-id="45aed-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="45aed-160">Development Edition 和。Commercial Suite，</span><span class="sxs-lookup"><span data-stu-id="45aed-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="45aed-161">功能</span><span class="sxs-lookup"><span data-stu-id="45aed-161">Features</span></span></th><th><span data-ttu-id="45aed-162">Development 版</span><span class="sxs-lookup"><span data-stu-id="45aed-162">Development Edition</span></span></th><th><span data-ttu-id="45aed-163">Commercial Suite，</span><span class="sxs-lookup"><span data-stu-id="45aed-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="45aed-164">裝置加密 (Bitlocker)</span><span class="sxs-lookup"><span data-stu-id="45aed-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-165">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-166">虛擬私人網路 (VPN)</span><span class="sxs-lookup"><span data-stu-id="45aed-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-167">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk 模式</a></span><span class="sxs-lookup"><span data-stu-id="45aed-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-169">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="45aed-170">管理和部署</span><span class="sxs-lookup"><span data-stu-id="45aed-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="45aed-171">行動裝置管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="45aed-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="45aed-172">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-173">封鎖取消註冊的能力</span><span class="sxs-lookup"><span data-stu-id="45aed-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-174">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-175">憑證為基礎的公司 Wi-fi 存取</span><span class="sxs-lookup"><span data-stu-id="45aed-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-176">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-177">Microsoft Store （消費者）</span><span class="sxs-lookup"><span data-stu-id="45aed-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-178">取用者</span><span class="sxs-lookup"><span data-stu-id="45aed-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-179">透過 MDM 進行篩選</span><span class="sxs-lookup"><span data-stu-id="45aed-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">企業市集入口網站</a></span><span class="sxs-lookup"><span data-stu-id="45aed-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-181">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="45aed-182">安全性和身分識別</span><span class="sxs-lookup"><span data-stu-id="45aed-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="45aed-183">使用 Azure Active Directory (AAD) 的登入</span><span class="sxs-lookup"><span data-stu-id="45aed-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-184">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-185">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-186">使用 Microsoft 帳戶 (MSA) 登入</span><span class="sxs-lookup"><span data-stu-id="45aed-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-187">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-188">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-189">下一步 的產生認證，使用 PIN 解除鎖定</span><span class="sxs-lookup"><span data-stu-id="45aed-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-190">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-191">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></span><span class="sxs-lookup"><span data-stu-id="45aed-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-193">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-194">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="45aed-195">服務與支援</span><span class="sxs-lookup"><span data-stu-id="45aed-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="45aed-196">自動系統更新到達</span><span class="sxs-lookup"><span data-stu-id="45aed-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-197">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="45aed-198">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span><span class="sxs-lookup"><span data-stu-id="45aed-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-200">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="45aed-201">長期維護分支</span><span class="sxs-lookup"><span data-stu-id="45aed-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="45aed-202">✔️</span><span class="sxs-lookup"><span data-stu-id="45aed-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="45aed-203">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="45aed-203">Prior release notes</span></span>
* [<span data-ttu-id="45aed-204">版本資訊-2016 5 月</span><span class="sxs-lookup"><span data-stu-id="45aed-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="45aed-205">版本資訊-2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="45aed-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="45aed-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45aed-206">See also</span></span>
* [<span data-ttu-id="45aed-207">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="45aed-207">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="45aed-208">商業功能</span><span class="sxs-lookup"><span data-stu-id="45aed-208">Commercial features</span></span>](commercial-features.md)
* [<span data-ttu-id="45aed-209">安裝工具</span><span class="sxs-lookup"><span data-stu-id="45aed-209">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="45aed-210">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="45aed-210">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
